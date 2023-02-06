<script lang="ts">
    import Navbar from '../components/Navbar.svelte';
    import PressButton from '../components/Buttons/PressButton.svelte';
    let value = ``;
    let result = "";
    let proper_json = false;
    let button_text = "Copy Result"
    $: result = handleChange(value);

    function isJson(str: string): boolean {
        try {
            JSON.parse(str);
        } catch (e) {
            proper_json = false;
            return false;
        }
        proper_json = true;
        return true;
    }
    function handleChange(str: string): string{
        if (isJson(str)){
            let parsed_obj = JSON.parse(str);
            return JSON.stringify(parsed_obj, null, 2);
        }
        else{
            return "Not proper Json"
        }
    }
    function copyText(str: string){
        navigator.clipboard.writeText(str);
    }
    function copyButtonFunction(){
        console.log("Copy Button pressed!")
        if (proper_json){
            copyText(result);
            button_text = "Result copied !";
            setTimeout(function () {
                button_text = "Copy Result";
            }, 5000);
        }
    }
</script>
<Navbar/>
<body>
    <div class="flex-container">
        <div class="flex-child-input">
            Input
            <form>
                <textarea bind:value={value}></textarea>
            </form>
        </div>
        
        <div class="flex-child-output">
            Result
            <div class="result-div">
                <textarea class="result-text" readonly>{result}</textarea>
            </div>
            
        </div>
    </div>
    <div class="button-div">
        <PressButton display_text={button_text} on:click={copyButtonFunction}/>
    </div>
</body>



    
<style>
    .button-div {
        display: flex;
        justify-content: center;
        height: 100%;
    }
    body {
        font-family: "apercu",sans-serif;
        background-color: #5CDB95;
    }
    .flex-container {
        display: flex;
        height: 500px;
        padding-bottom: 5%
    }
    form{
        padding-top: 14px;
        padding-right: 5px;
        height: 100%;
    }
    textarea {
        display: flex;
        border: 0px;
        height: 100%;
        width: 100%;
        background-color: #edf5e1;
    }
    .result-div {
        display: flex;
        padding-top: 14px;
        height: 100%
    }
    .result-text {
        background-color: #379683;
        height: 100%;
        color: rgb(255, 255, 255);
    }
    .flex-child-input {
        flex: 1;
        height: 100%;
        background-color: #5CDB95;
    }
    .flex-child-output {
        flex: 1;
        height: 100%;
        background-color: #5CDB95;
        padding-top: 0px;
    }
</style>