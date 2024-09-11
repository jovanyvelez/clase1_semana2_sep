<script lang="ts">
    let items: HTMLElement[] = [];
    let active = 3;

    const loadShow = () => {
        let stt = 0;
        items[active].style.transform = `none`;
        items[active].style.zIndex = '1';
        items[active].style.filter = 'none';
        items[active].style.opacity = '1';
        for (let i = active + 1; i < items.length; i++) {
            stt++;
            items[i].style.transform = `translateX(${120 * stt}px) scale(${1 - 0.2 * stt}) perspective(16px) rotateY(-1deg)`;
            items[i].style.zIndex = (-stt).toString();
            items[i].style.filter = 'blur(5px)';
            items[i].style.opacity = (stt > 2 ? 0 : 0.6).toString();
        }
        stt = 0;
        for (let i = active - 1; i >= 0; i--) {
            stt++;
            items[i].style.transform = `translateX(${-120 * stt}px) scale(${1 - 0.2 * stt}) perspective(16px) rotateY(1deg)`;
            items[i].style.zIndex = (-stt).toString();
            items[i].style.filter = 'blur(5px)';
            items[i].style.opacity = (stt > 2 ? 0 : 0.6).toString();
        }
    };

    const next = () => {
        active = active + 1 < items.length ? active + 1 : active;
        loadShow();
    };

    const prev = () => {
        active = active - 1 >= 0 ? active - 1 : active;
        loadShow();
    };

    
    $effect(() => {
        items = Array.from(document.querySelectorAll('.slider .item'));
        loadShow();
	});
</script>

<div class="slider">
    <div class="item">
        <h1>Slide 1</h1>
        Lorem ipsum dolor sit amet consectetur, adipisicing elit. Facere magni magnam unde ipsam repudiandae explicabo expedita labore, sequi minus neque beatae voluptatum, quasi accusamus quia quis voluptas laborum ad! Ab totam doloribus, excepturi possimus rem vel quia fugit molestiae officiis!
    </div>
    <div class="item">
        <h1>Slide 2</h1>
        Lorem ipsum dolor sit amet consectetur, adipisicing elit. Facere magni magnam unde ipsam repudiandae explicabo expedita labore, sequi minus neque beatae voluptatum, quasi accusamus quia quis voluptas laborum ad! Ab totam doloribus, excepturi possimus rem vel quia fugit molestiae officiis!
    </div>
    <div class="item">
        <h1>Slide 3</h1>
        Lorem ipsum dolor sit amet consectetur, adipisicing elit. Facere magni magnam unde ipsam repudiandae explicabo expedita labore, sequi minus neque beatae voluptatum, quasi accusamus quia quis voluptas laborum ad! Ab totam doloribus, excepturi possimus rem vel quia fugit molestiae officiis!
    </div>
    <div class="item">
        <h1>Slide 4</h1>
        Lorem ipsum dolor sit amet consectetur, adipisicing elit. Facere magni magnam unde ipsam repudiandae explicabo expedita labore, sequi minus neque beatae voluptatum, quasi accusamus quia quis voluptas laborum ad! Ab totam doloribus, excepturi possimus rem vel quia fugit molestiae officiis!
    </div>
    <div class="item">
        <h1>Slide 5</h1>
        Lorem ipsum dolor sit amet consectetur, adipisicing elit. Facere magni magnam unde ipsam repudiandae explicabo expedita labore, sequi minus neque beatae voluptatum, quasi accusamus quia quis voluptas laborum ad! Ab totam doloribus, excepturi possimus rem vel quia fugit molestiae officiis!
    </div>
    <div class="item">
        <h1>Slide 6</h1>
        Lorem ipsum dolor sit amet consectetur, adipisicing elit. Facere magni magnam unde ipsam repudiandae explicabo expedita labore, sequi minus neque beatae voluptatum, quasi accusamus quia quis voluptas laborum ad! Ab totam doloribus, excepturi possimus rem vel quia fugit molestiae officiis!
    </div>
    <div class="item">
        <h1>Slide 7</h1>
        Lorem ipsum dolor sit amet consectetur, adipisicing elit. Facere magni magnam unde ipsam repudiandae explicabo expedita labore, sequi minus neque beatae voluptatum, quasi accusamus quia quis voluptas laborum ad! Ab totam doloribus, excepturi possimus rem vel quia fugit molestiae officiis!
    </div>
    <button onclick={next} id="next"> next </button>
    <button onclick={prev} id="prev"> prev </button>
</div>

<style>

.slider{
    position: relative;
    width: 100%;
    height: 370px;
    overflow: hidden;
}
.item{
    position: absolute;
    width: 200px;
    height: 320px;
    text-align: justify;
    background-color: #fff;
    border-radius: 10px;
    padding: 20px;
    transition: 0.5s;
    left: calc(50% - 110px);
    top: 0;
}
#next, #prev{
    position: absolute;
    top: 40%;
    color: black;
    opacity: 0.3;
    background-color: transparent;
    border: none;
    font-size: xxx-large;
    font-family: monospace;
    font-weight: bold;
    left: 400px;
}
#next{
    left: unset;
    right: 400px;
}
</style>
