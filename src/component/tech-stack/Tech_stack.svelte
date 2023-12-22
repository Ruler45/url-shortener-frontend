
<script>
    export let imageUrl="path/to/image";
    export let desc="Tech Stack Description";
    export let title="Tech Stack Title";
    export let Url="https://www.google.com";
</script>


<div class="Tech-box">
    <a href={Url} target="_blank" class="tech-stack_logo"> 
        <img class="logoImage" src={imageUrl} alt=""> 
        <h4>{title}</h4> 
    </a>
    <div class="tech-stack_desc"> {desc}  </div>
</div>

<style>
    .Tech-box{
        display: flex;
        flex-direction: row;
        gap: 20px;
        width: 70%;
        height: 150px;
        border: solid 1px rgb(17, 112, 237);
        border-radius: 5px;
        padding: 1rem;
        transition: 0.3s ease-in-out;

        &:hover{
            background-color: rgba(144, 212, 249, 0.968);
            border-radius: 10px;
            backdrop-filter: blur(5px);
        }
    }
    .tech-stack_logo{
        display: flex;
        flex-direction: column;
        align-items: center;
        width: 20%;
        height: 100%;
        border-radius: 5px;
        /* padding: 1rem; */
        overflow: hidden;
        text-decoration: none;
        color: black;
    }
    .logoImage{
        width: 70%;
        height: 70%;
        object-fit: contain;
        margin: 5px auto;
    }
    .tech-stack_desc{
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        width: 80%;
        height: 100%;
        font-size: 1rem;
        border-radius: 5px;

    }
    </style>