<template>
    <div id>
        <header>
            <h1>HeaDer</h1>
            <h2>Subtitle</h2>
            <h4>HTML5 ROCKS</h4>
        </header>
        <div id="container">
            <nav>
                <h3>Nav</h3>
                <a href="#">Link1</a>
                <a href="#">Link2</a>
                <a href="#">Link3</a>
            </nav>
            <section>
                <article>
                    <header>
                        <h1>Article Head</h1>
                    </header>
                    <p>Lorem ipsum dolor Html5 nunc aut nunquam sit amet,consectetur adipiscing elit.Vivamus at est eros,vel frinailla urna</p>
                    <p>Lorem ipsum dolor Html5 nunc aut nunquam sit amet,consectetur adipiscing elit.Vivamus at est eros,vel frinailla urna</p>
                    <footer>
                        <h2>Article footer</h2>
                    </footer>
                </article>
                <article>
                    <header>
                        <h1>Article Head</h1>
                    </header>
                    <p>Lorem ipsum dolor Html5 nunc aut nunquam sit amet,consectetur adipiscing elit.Vivamus at est eros,vel frinailla urna</p>
                    <footer>
                        <h2>Article footer</h2>
                    </footer>
                </article>
            </section>
            <aside>
                <h3>Aside</h3>
                <p>Lorem ipsum dolor Html5 nunc aut nunquam sit amet,consectetur adipiscing elit.Vivamus at est eros,vel frinailla urna</p>
            </aside>
            <footer>
                <h2>Footer</h2>
            </footer>
        </div>
    </div>
</template>
 
<script>
export default {
    name: "",
    props: {},
    components: {},
    data() {
        return {};
    },
    mounted() {},
    computed: {},
    methods: {},
    watch: {},
    filters: {}
};
</script>
 
<style>
body {
    background-color: #ccc;
    font-family: Verdana, Geneva, Tahoma, sans-serif;
    margin: 0 auto;
    max-width: 900px;
    border: solid;
    border-color: #fff;
}
header {
    background-color: #f47d31;
    display: block;
    color: #fff;
    text-align: center;
}
header h2 {
    margin: 0px;
}
h1,
h2,
h3 {
    margin: 0px;
}
h1 {
    font-size: 72px;
}
h2 {
    font-size: 24px;
    text-align: center;
    color: #f47d31;
}
h3 {
    font-size: 18px;
    text-align: center;
    color: #f47d31;
}
h4 {
    color: #f47d31;
    background-color: #fff;
    box-shadow: 2px 2px 20px #888;
    transform: rotate(-45deg);
    position: absolute;
    padding: 0 150px;
    top: 50px;
    left: -120px;
    text-align: center;
}
nav {
    display: block;
    width: 25%;
    float: left;
}
nav a:link,
nav a:visited {
    display: block;
    border-bottom: 3px solid #fff;
    padding: 10px;
    text-decoration: none;
    font-weight: bold;
    margin: 5px;
}
nav a:hover {
    color: white;
    background-color: #f47d31;
}
nav h3 {
    margin: 15px;
    color: #fff;
}
#container {
    background-color: #888;
}
section {
    display: block;
    width: 50%;
    float: left;
}
article {
    background-color: #eee;
    display: block;
    margin: 10px;
    padding: 10px;
    border-radius: 10px;
    box-shadow: 2px 2px 20px #888;
    transform: rotate(-10deg);
}
article header {
    border-radius: 10px;
    padding: 5px;
}
article footer {
    border-radius: 10px;
    padding: 5px;
}
article h1 {
    font-size: 18px;
}
aside {
    display: block;
    width: 25%;
    float: left;
}
aside h3,
aside p {
    margin: 15px;
    color: white;
}
aside p {
    font-weight: bold;
    font-style: italic;
}
footer {
    clear: both;
    display: block;
    background-color: #f47d31;
    color: #fff;
    text-align: center;
    padding: 15px;
}
footer h2 {
    font-size: 14px;
    color: white;
}
a {
    color: #f47d31;
}
a:hover {
    text-decoration: underline;
}
</style>

 