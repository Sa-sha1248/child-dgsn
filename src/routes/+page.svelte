<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Nanum+Brush+Script&display=swap" rel="stylesheet">

<style>
    /* 글씨체 */
        /* 말씀내용 */
        #content {
            color: black;
            font-family: 'Nanum Brush Script', cursive;
            font-weight: bold;
            font-size: 5em;
        }
        /* 장, 절 */
        #location{
            color: black;
            font-family: 'Nanum Brush Script', cursive;
            font-size: 3em;
        }
        /* 네비게이션 */
        .nav_content{
            color: black;
            font-family: 'Nanum Brush Script', cursive;
            font-size: 2em;
        }

    /* 네비게이션 바 */
    #nav_bar{
        margin: 20px;
    }

    .nav_content{
        padding: 10px;
        display: inline;
        background-color: transparent;
        border: none;
        /* background-color: rgb(245, 169, 182);
        border-style: solid;
        border-color: rgb(245, 169, 182);
        border-radius: 60px; */
        
    }

    .hidden{
        display: none;

    }
    /* .content-changer{

    } */

    .close-button{
        display: block;
        margin-top: 10px;
        margin-bottom: 10px;
    }

    .color{
        height: 50px;
        width: 50px;
        border-radius: 20%;
        border-color: azure;
    }
    /* 말씀 구절 부분 위치 조절 */
    #content {
        margin: 0;
		
	}

    #location{
        margin: 0;
    }

    #vertical-grid{
        display: grid;
        width: 100vw;
        height: 100vh;
        grid-template-rows: 1.3fr 1fr 1fr;
    }

    #content_box, .trash{      
        text-align: center;
    }


</style>

<script>
    let p = '말씀구절';
    let chapter = 1;
    let verse = 2;

    function hide(params) {
        let container = document.getElementById(params);
        container.classList.add('hidden');
    }

    function color_change(params) {
        document.body.style.backgroundColor = params;
    }

</script>


<div id = vertical-grid>
    <div id = 'nav_bar'>
        <!-- 클릭하면 숨겨진 div를 열어서 내용 변경할 수 있도록 하기 -->
        <button class = 'nav_content' on:click={() => document.getElementById('content-changer').classList.remove('hidden')}>말씀내용 변경하기</button>
            
        <button class = 'nav_content' on:click={() => document.getElementById('font-changer').classList.remove('hidden')}>글씨체 변경</button>
           
        <button class = 'nav_content' on:click={() => document.getElementById('background-changer').classList.remove('hidden')}>배경 색 바꾸기</button>
        
        <div style="margin: 10px;">
            <div id = 'content-changer' class = 'hidden' >
                구절내용 <input bind:value={p}>
                <input bind:value = {chapter}/> 장
                <input bind:value = {verse}/> 절

                <button class = "close-button" on:click={ () => hide('content-changer')}>닫기</button>
            </div>

            <div id = 'font-changer' class = 'hidden' >
                아직 안만듬
                <button class = "close-button" on:click={ () => hide('font-changer')}>닫기</button>
            </div>

            <div id = 'background-changer' class = 'hidden' >

                <button class = 'color' on:click={ () => color_change('red')} style = 'background-color:red'>  </button>
                <button class = 'color' on:click={ () => color_change('yellow')} style = 'background-color:yellow'>  </button>
                <button class = 'color' on:click={ () => color_change('blue')} style = 'background-color:blue'>  </button>
                <button class = 'color' on:click={ () => color_change('gray')} style = 'background-color:gray'>  </button>
                <button class = 'color' on:click={ () => color_change('white')} style = 'background-color:white'>  </button>
                <button class = 'color' on:click={ () => color_change('pink')} style = 'background-color:pink'>  </button>
                <button class = 'color' on:click={ () => color_change('brown')} style = 'background-color:brown'>  </button>

                <button class = "close-button" on:click={ () => hide('background-changer')}>닫기</button>
            </div>
        </div>
    </div>

    <div id = 'content_box'>
        <div id = 'content'>{p}</div>

        <div id = 'location'>
            {chapter}장 {verse}절
        </div>

    </div>
    <div class = 'trash'></div>
</div>