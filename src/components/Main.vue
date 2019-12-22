/* eslint-disable no-console */
<template>
  <div>
    <div class="header">
      <h1>JS Highlighter</h1>
    </div>
    <div class="inputDiv" >
        <textarea id="codeText" placeholder="Your code here"/> <br>
        <button @click="getHTML" >Submit</button>
    </div>
    <center>
      <div id="outputDiv" class="outputDiv"></div>
      <button @click="copyHTML" >Copy HTML</button>
    </center>
  </div>
</template>

<script>
/* eslint-disable no-console */
import Prism from 'prismjs'

export default {
  name: 'Main',
  methods: {
    getHTML() {
      const codeTextarea = document.getElementById('codeText')
      let codeText = codeTextarea.value
      const hHTML = Prism.highlight(codeText, Prism.languages.javascript, 'javascript')
      const outputDiv = document.getElementById('outputDiv')
      outputDiv.innerHTML = hHTML
    }, 
    copyHTML() {
      const htmlcode = document.getElementById('outputDiv').innerHTML
      var el = document.createElement('textarea');
      el.value = htmlcode;
      el.setAttribute('readonly', '');
      el.style = {position: 'absolute', left: '-9999px'};
      document.body.appendChild(el);
      el.select();
      document.execCommand('copy');
      document.body.removeChild(el);
    }
  }
}
</script>

<style scoped>

  @import url('https://fonts.googleapis.com/css?family=Open+Sans:400,800&display=swap');

  .header {
    width: 100%;
    min-height: 40px;
    background: linear-gradient(90deg, rgba(2,0,36,1) 0%, rgba(142,237,200,1) 0%, rgba(20,236,234,1) 100%); 
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Open Sans';
    color: #151522;
    font-size: 14px;
    padding: 6px 0px 6px 0px;
  }

  .inputDiv {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 20px 0px;
  }

  textarea {
    width: 60%;
    height: 200px;
    padding: 6px;
    border-radius: 4px;
    font-family: monospace;
    font-size: 1.1em;
    outline: none;
    box-sizing: border-box;
    border: 2px solid #75DA8B;
    transition: .3s;
    padding-left: 12px;
    background-color: #ebfff3;
    resize: none;
  }

  textarea:focus {
    border-color: #019031;
    box-shadow: 0px 0px 8px 0px #019031;
  }

  button {
    width: 60%;
    padding: 10px 0px;
    border-radius: 4px;
    outline: none;
    box-sizing: border-box;
    background-color: #75DA8B;
    border: 2px solid #75DA8B;
    transition: .2s;
    margin-top: 10px;
    font-size: 14px;
    font-weight: 700;
  }

  button:hover {
    border: 2px solid #019031;
    box-shadow: 0px 0px 4px 0px #019031;
  }

  .outputDiv {
    width: 60%;
    background-color: #f1f3f5;
    padding: 10px 0px;
    border-radius: 4px;
  }

  @media only screen and (max-width: 600px) {
    textarea {
      width: 85%;
    }
    button {
      width: 85%;
      margin-top: 4px;
    }
    .outputDiv {
      width: 85%;
    }
  }

</style>