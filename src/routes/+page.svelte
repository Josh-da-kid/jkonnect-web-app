<script lang='ts'>
import { onMount } from 'svelte';
       let showMenu = false;
       let showOverlay = true;
    
    
    // List of songs
    
    let isPlaying: boolean = true; // Default: Sound is ON
        let audio: HTMLAudioElement | null = null; // Explicitly typed
        let currentSongIndex: number = 0;
    
        // List of songs (Replace with actual paths)
        const songs: string[] = [
            '/yvSG60yjYQoz.128.mp3',
            '/R2k83VTIyoPd.128.mp3',
            '/I9xUTg6dvvUg.128.mp3'
        ];
    
        // Function to play the next song
        function playNextSong() {
            if (!audio) return;
            currentSongIndex = (currentSongIndex + 1) % songs.length;
            audio.src = songs[currentSongIndex];
            if (isPlaying) audio.play();
        }
    
        // Toggle sound ON/OFF
        function toggleSound() {
            if (!audio) return;
            if (isPlaying) {
                audio.pause();
            } else {
                audio.play();
            }
            isPlaying = !isPlaying;
        }
    
        // Initialize audio on component mount
        onMount(() => {
    audio = document.getElementById("audioPlayer") as HTMLAudioElement;

    if (audio) {
        audio.muted = true; // Ensure it starts muted
        audio.play().then(() => {
            console.log("Autoplay started");
        }).catch(error => {
            console.error("Autoplay blocked:", error);
        });
    }
});

function unmuteAudio() {
    if (audio) {
        audio.muted = false; // Unmute when user interacts
        audio.play();
    }
}
    </script>




<!-- Header Section -->
 
 <section class="bg-black fixed w-full left-0 right-0 bg-opacity-80 mt-0 shadow-lg top-0 z-100 mb-5">

   
     <div class="flex mx-auto text-white justify-between p-5 px-6">
        {#if !showOverlay}
         <div class="ml-2">
             <h1 class="text-2xl" ><span class="text-green-500 text-3xl font-bold ">J</span><span class="mr-2">osiah's</span><span class="text-green-500">P</span>ortfolio</h1>
         </div>

         <div class="mr-10 hidden sm:flex sm:mr-0 md:mr- sm:mt-2">
             <ul class="flex gap-12">
                <li class="hover:text-green-400 cursor-pointer ml-3"><a href="#home">Home</a></li>
                 <li class="hover:text-green-400 cursor-pointer"><a href="#about">About</a></li>
                 <li class="hover:text-green-400 cursor-pointer"><a href="#projects">Projects</a></li>
                 <li class="hover:text-green-400 cursor-pointer"><a href="#skills">Skills</a></li>
                 <li class="hover:text-green-400 cursor-pointer"><a href="#services">Services</a></li>
                 <li class="hover:text-green-400 cursor-pointer"><a href="#contact">Contact</a></li>
             </ul>
         </div>
         

         <!-- HAMBURGER MENU -->
          {#if !showMenu}
         <div class="sm:hidden text-lg" id="menu-btn">
             <button on:click={() => {
                showMenu = !showMenu;
             }}>
                <svg class="w-11 h-11 mr-8 hover:text-green-400" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24"><path fill="currentColor" d="M3 6h18v2H3zm0 5h18v2H3zm0 5h18v2H3z"/></svg>
            </button>
        </div>

            {:else}
            <!-- THE X BUTTON -->
            <div class="" >
                <button on:click={() => {
                    showMenu = !showMenu;
                            }}>
                    <svg class="hover:text-red-500 text-white ml-6" id="x" xmlns="http://www.w3.org/2000/svg" width="35" height="35" viewBox="0 0 24 24"><path fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M6.758 17.243L12.001 12m5.243-5.243L12 12m0 0L6.758 6.757M12.001 12l5.243 5.243"/></svg>
                </button>   
            </div>
            {/if}
            {/if}
                    
     </div>

     <div></div>
    </section>

     <!-- MOBILE MENU -->
      {#if showMenu}
     <div id="mobile-menu" class="mx-auto z-80 text-white p-5 px-6 h-screen bg-black bg-opacity-50 fixed inset-0 text-center justify-center items-center">

        <div class="mr-10 space-y-6" >
            
              <p class="cursor-pointer ml-3 mt-32"><a on:click={() => showMenu = false} class="hover:text-green-400" href="#home">Home</a></p>
                <p class="cursor-pointer"><a on:click={() => showMenu = false} class="hover:text-green-400 " href="#about">About</a></p>
                <p class="cursor-pointer"><a  on:click={() => showMenu = false} class="hover:text-green-400 " href="#projects">Projects</a></p>
                <p class="cursor-pointer"><a  on:click={() => showMenu = false} class="hover:text-green-400 " href="#skills">Skills</a></p>
                <p class="cursor-pointer"><a  on:click={() => showMenu = false} class="hover:text-green-400 " href="#services">Services</a></p>
                <p class="cursor-pointer"><a  on:click={() => showMenu = false} class="hover:text-green-400 " href="#contact">Contact</a></p>

        </div>
        </div>
        {/if}
 
<!-- Overlay to show button on top of everything -->
{#if showOverlay}
<div class="fixed inset-0 bg-black bg-opacity-60 flex items-center justify-center z-50">
    <div class="text-center justify-center items-center space-y-4">
        <div class="flex text-center justify-center items-center gap-3">

            <span class="text-3xl font-bold">Built with</span>
            <span><img class="h-20 w-20" src="/svelte-icon-1703x2048-c1sw8yt9.png" alt=""></span>
        </div>
        <button id="viewBtn" on:click={() => {
            unmuteAudio()
            showOverlay = false
        }} class="bg-green-600 text-white px-6 py-3 rounded-full shadow-lg text-xl hover:bg-green-700">
             View Portfolio
        </button>
    </div>
</div>
{/if}


<!-- Body -->
 <section id="home" class="mt-32 sm:mt-24 text-white">
    
<div class="text-white font-bold rounded-full w-[350px] sm:m-12 m-4 p-4 flex gap-2 border focus-none border-gray-700">
    
        <span>
        <svg  xmlns="http://www.w3.org/2000/svg" width="50" height="50" viewBox="0 0 50 50"><g fill="none" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"><path stroke="#344054" d="M25 6.25V25"/><path stroke="#306cfe" d="M36.792 15.292a16.667 16.667 0 1 1-23.584 0"/></g></svg>

    </span>
           
    <p class="flex text-center mt-3">Welcome to my Creative Space</p>
</div>


<div class="m-4 mt-8 flex gap-2 text-center justify-center border-gray-700 hover:bg-gray-800 hover:text-green-500 cursor-pointer border p-3 rounded-full w-[200px]">

    <a class="flex" href="/" download>

        <span class="">
            <svg xmlns="http://www.w3.org/2000/svg" width="28" height="26" viewBox="0 0 24 24"><path fill="currentColor" d="m12 15.577l-3.539-3.538l.708-.72L11.5 13.65V5h1v8.65l2.33-2.33l.709.719zM6.616 19q-.691 0-1.153-.462T5 17.384v-2.423h1v2.423q0 .231.192.424t.423.192h10.77q.23 0 .423-.192t.192-.424v-2.423h1v2.423q0 .691-.462 1.153T17.384 19z"/></svg>
        </span>
        
            <span>DOWNLOAD CV</span>

    </a>
</div>

<div class="sm:text-5xl text-4xl md:text-6xl mt-12 ml-6 text-gray-300">
<h1>Hi, I'm </h1>
<span class="animate-typing"></span>
</div>

<script src="https://unpkg.com/typed.js@2.1.0/dist/typed.umd.js"></script>
<script>
  // Wait for the user to click the button
  document.getElementById("viewBtn").addEventListener("click", function() {
    // Hide the overlay
    
    
    // Initialize Typed.js only after the overlay is dismissed
    let typing = new Typed(".animate-typing", {
      strings: ["Josiah Andrew", "a web developer", "a Full-stack developer"],
      typeSpeed: 160,
      backSpeed: 150,
      loop: true
    });
  });
</script>


<div class="ml-6 mt-8 font-mono lg:flex justify-between">

    <div class="space-y-3">

        <div class="flex gap-3">
            <span class="border w-11 h-11 sm:w-18 sm:h-18 p-3 rounded-full">
                <svg xmlns="http://www.w3.org/2000/svg" width="3em" height="3em" viewBox="0 0 512 512"><path fill="currentColor" d="M477.64 38.26a4.75 4.75 0 0 0-3.55-3.66c-58.57-14.32-193.9 36.71-267.22 110a317 317 0 0 0-35.63 42.1c-22.61-2-45.22-.33-64.49 8.07C52.38 218.7 36.55 281.14 32.14 308a9.64 9.64 0 0 0 10.55 11.2l87.31-9.63a194 194 0 0 0 1.19 19.7a19.53 19.53 0 0 0 5.7 12L170.7 375a19.6 19.6 0 0 0 12 5.7a194 194 0 0 0 19.59 1.19l-9.58 87.2a9.65 9.65 0 0 0 11.2 10.55c26.81-4.3 89.36-20.13 113.15-74.5c8.4-19.27 10.12-41.77 8.18-64.27a317.7 317.7 0 0 0 42.21-35.64C441 232.05 491.74 99.74 477.64 38.26M294.07 217.93a48 48 0 1 1 67.86 0a47.95 47.95 0 0 1-67.86 0"/><path fill="currentColor" d="M168.4 399.43c-5.48 5.49-14.27 7.63-24.85 9.46c-23.77 4.05-44.76-16.49-40.49-40.52c1.63-9.11 6.45-21.88 9.45-24.88a4.37 4.37 0 0 0-3.65-7.45a60 60 0 0 0-35.13 17.12C50.22 376.69 48 464 48 464s87.36-2.22 110.87-25.75A59.7 59.7 0 0 0 176 403.09c.37-4.18-4.72-6.67-7.6-3.66"/></svg>
            </span>
    
            <p class="sm:mt-6 mb-3">Transforming ideas into digital reality</p>
        </div>
    
        <div class="flex gap-3">
            <span class="border w-10 h-10 sm:w-15 sm:h-15 p-3 rounded-full ml-11">
                <svg xmlns="http://www.w3.org/2000/svg" width="2em" height="2em" viewBox="0 0 32 32"><path fill="currentColor" d="M29.502 3.415a3.56 3.56 0 0 0-4.974-.09L11.043 16.032l-.014-.002l-2.129 2.1a2 2 0 0 0-.389.538a3.98 3.98 0 0 0-2.365.683A4.91 4.91 0 0 0 3.7 23.559a2.67 2.67 0 0 1-.7 1.925l-.789.739l-.059.324a1.473 1.473 0 0 0 1.023 1.677l2.579.783l.5.1q.623.115 1.257.115a7.02 7.02 0 0 0 5.39-2.527c.574-.684.9-1.539.93-2.426c.25-.095.486-.244.69-.444l.798-.788l.015.03L29.527 8.39a3.56 3.56 0 0 0-.025-4.974m-14.608 17.23l-2.81-2.846L25.9 4.78a1.559 1.559 0 0 1 2.19 2.218zm-8.28 6.496l-.33-.061L4.7 26.6a4.9 4.9 0 0 0 .988-2.813a2.99 2.99 0 0 1 1.546-2.758a2 2 0 0 1 2.559.232l1.454 1.459a2 2 0 0 1 .117 2.694a5.02 5.02 0 0 1-4.75 1.727"/></svg>
            </span>
    
            <p class="sm:mt-4 mb-3">Creating elegant and responsive designs</p>
    
        </div>
    
        <div class="flex gap-3">
            <span class="border p-2 w-8 h-8 sm:w-13 sm:h-13 rounded-full sm:ml-21">
                <svg class="text-center justify-center items-center mx-auto" xmlns="http://www.w3.org/2000/svg" width="2em" height="2em" viewBox="0 0 24 24"><path fill="currentColor" d="M19.43 12.98c.04-.32.07-.64.07-.98s-.03-.66-.07-.98l2.11-1.65c.19-.15.24-.42.12-.64l-2-3.46c-.12-.22-.39-.3-.61-.22l-2.49 1c-.52-.4-1.08-.73-1.69-.98l-.38-2.65C14.46 2.18 14.25 2 14 2h-4c-.25 0-.46.18-.49.42l-.38 2.65c-.61.25-1.17.59-1.69.98l-2.49-1c-.23-.09-.49 0-.61.22l-2 3.46c-.13.22-.07.49.12.64l2.11 1.65c-.04.32-.07.65-.07.98s.03.66.07.98l-2.11 1.65c-.19.15-.24.42-.12.64l2 3.46c.12.22.39.3.61.22l2.49-1c.52.4 1.08.73 1.69.98l.38 2.65c.03.24.24.42.49.42h4c.25 0 .46-.18.49-.42l.38-2.65c.61-.25 1.17-.59 1.69-.98l2.49 1c.23.09.49 0 .61-.22l2-3.46c.12-.22.07-.49-.12-.64l-2.11-1.65zM12 15.5c-1.93 0-3.5-1.57-3.5-3.5s1.57-3.5 3.5-3.5s3.5 1.57 3.5 3.5s-1.57 3.5-3.5 3.5z"><animateTransform attributeName="transform" attributeType="XML" dur="10s" from="0 12 12" repeatCount="indefinite" to="360 12 12" type="rotate"/></path></svg>
            </span>
    
        <p class="sm:mt-4">Building robust and scalable solutions</p>
        
        </div>
    </div>

    <!-- MY PICTURE -->
     <div class="lg:mt-0 flex mt-12 mx-auto text-center justify-center items-center">
        <img class="rounded-full w-80 h-80" src="/462567462_1109103804192810_1284484715818841119_n.jpg" alt="">

     </div>

</div>
 </section>

 <!-- ABOUT ME -->
 <section id="about" class="p-3 justify-center items-center mx-auto">
    <div class="text-4xl sm:text-5xl md:text-6xl text-center mt-21 items-center">

        <h1>About me</h1>

        <div class="flex justify-center items-center h-full w-full ">
            <svg class="h-8 " xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" viewBox="0 0 24 24">
                <circle cx="18" cy="12" r="0" fill="#78d65c">
                    <animate attributeName="r" begin=".67" calcMode="spline" dur="1.5s" keySplines="0.2 0.2 0.4 0.8;0.2 0.2 0.4 0.8;0.2 0.2 0.4 0.8" repeatCount="indefinite" values="0;2;0;0"/>
                </circle>
                <circle cx="12" cy="12" r="0" fill="#78d65c">
                    <animate attributeName="r" begin=".33" calcMode="spline" dur="1.5s" keySplines="0.2 0.2 0.4 0.8;0.2 0.2 0.4 0.8;0.2 0.2 0.4 0.8" repeatCount="indefinite" values="0;2;0;0"/>
                </circle>
                <circle cx="6" cy="12" r="0" fill="#78d65c">
                    <animate attributeName="r" begin="0" calcMode="spline" dur="1.5s" keySplines="0.2 0.2 0.4 0.8;0.2 0.2 0.4 0.8;0.2 0.2 0.4 0.8" repeatCount="indefinite" values="0;2;0;0"/>
                </circle>
            </svg>

        </div>

        
    </div>

    <div class="relative sm:w-[500px] w-full lg:mt-0 mx-auto mt-4 group flex items-center">
        {#if !showMenu}
        <img class="hidden sm:flex transition-all duration-300 ease-in-out" src="/WhatsApp Image 2024-12-25 at 12.24.20 PM.jpeg" alt="about me info">
    
        <!-- about text -->
        <div class="sm:absolute inset-0 justify-center p-1 sm:p-3 shadow-lg shadow-green-500 items-center bg-black opacity-60">
            <p class="aboutMe bg-black text-lg sm:text-xl font-bold">
                Hey there! My name is Josiah Andrew, a passionate Full-Stack Web Developer with a keen eye for detail and a commitment to creating efficient, scalable, and user-friendly applications. Born on January 12, 2008, I have always been fascinated by technology and its ability to solve real-world problems. My journey into web development has equipped me with expertise in both frontend and backend technologies, allowing me to build seamless digital experiences. I am constantly learning and evolving, staying up to date with the latest industry trends to refine my skills. My goal is to create impactful solutions that not only meet business needs but also enhance user experiences. <br>
                <span class="font-extrabold text-green-600 mt-3">Let’s build something incredible together!!</span>
            </p> 
        </div>
        {/if}
    </div>
  </section>

 <!-- MY FEATURED PROJECTS -->
  <section id="projects" class="justify-center items-center place-self-center">
    <div class="text-4xl sm:text-5xl md:text-6xl text-center mt-21 items-center justify-center">

        <h1>Featured Projects</h1>

        <div class="flex justify-center items-center h-full w-full text-4xl">
            <svg class="h-8 " xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" viewBox="0 0 24 24">
                <circle cx="18" cy="12" r="0" fill="#78d65c">
                    <animate attributeName="r" begin=".67" calcMode="spline" dur="1.5s" keySplines="0.2 0.2 0.4 0.8;0.2 0.2 0.4 0.8;0.2 0.2 0.4 0.8" repeatCount="indefinite" values="0;2;0;0"/>
                </circle>
                <circle cx="12" cy="12" r="0" fill="#78d65c">
                    <animate attributeName="r" begin=".33" calcMode="spline" dur="1.5s" keySplines="0.2 0.2 0.4 0.8;0.2 0.2 0.4 0.8;0.2 0.2 0.4 0.8" repeatCount="indefinite" values="0;2;0;0"/>
                </circle>
                <circle cx="6" cy="12" r="0" fill="#78d65c">
                    <animate attributeName="r" begin="0" calcMode="spline" dur="1.5s" keySplines="0.2 0.2 0.4 0.8;0.2 0.2 0.4 0.8;0.2 0.2 0.4 0.8" repeatCount="indefinite" values="0;2;0;0"/>
                </circle>
            </svg>
        </div>
        </div>

        <p class="text-center text-xl p-3">A showcase of some of my best work, built using Svelte, Firebase, and Tailwind CSS.</p>

        <div class="block p-8 lg:grid lg:grid-cols-3  space-y-4 lg:space-y-0 lg:space-x-4 text-lg">
            <div class="border focus-none border-green-500 shadow-lg shadow-green-500 p-4">

                <p class="text-2xl font-bold text-green-600 text-center">Svelte Task App</p>
                <ol class="mt-6 space-y-5">

                    <p><span class="text-green-600 font-bold">Tech Stack:</span> <span>Svelte, Tailwind CSS, and Javascript</span></p>

                    <p><span><span class="text-green-600 font-bold">Description:</span> <span>A basic tasks app, helping you to keep track of things you'll need to do.</span></span></p>

                    <p><span class="text-green-600 font-bold">Features:</span> <span>Add, Remove and tag completed tasks.</span></p>

                    <p><span class="text-green-600 font-bold">Live Demo:</span> <a class="underline text-gray-300" target="_blank" href="https://jkonnect-svelte-project.vercel.app/">click here</a></p>
                    <p><span class="text-green-600 font-bold">GitHub Repo:</span> <a class="underline text-gray-300" target="_blank" href="https://github.com/Josh-da-kid/svelte-project">click here</a>
                    </p>
                </ol>
            </div>

<div class="border p-4 border-green-500 shadow-lg shadow-green-500">

    <p class="text-2xl font-bold text-green-600 text-center">Learn $ Earn Hub</p>
                <ol class="mt-6 space-y-5">

                    <p><span class="text-green-600 font-bold">Tech Stack:</span> <span>Firebase, Tailwind CSS, and Javascript</span></p>

                    <p><span><span class="text-green-600 font-bold">Description:</span> <span>An educational platform where you learn interesting subjects and earn cool cash for simply taking quizzes.</span></span></p>

                    <p><span class="text-green-600 font-bold">Features:</span> <span>Learn interesting topics, Earn by taking quizzes, and grow as you learn.</span></p>

                    <!-- <p><span class="text-green-600 font-bold">Live Demo:</span> <a class="underline text-gray-300" target="_blank" href="/">click here</a></p> -->
                    <p><span class="text-green-600 font-bold">GitHub Repo:</span> <a class="underline text-gray-300" target="_blank" href="https://github.com/Josh-da-kid/Learn2Earn">click here</a>
                    </p>
                </ol>
</div>

<div class="border p-4 border-green-500 shadow-lg shadow-green-500">

     <p class="text-2xl font-bold text-green-600 text-center">Web Portfolio</p>
                <ol class="mt-6 space-y-5">

                    <p><span class="text-green-600 font-bold">Tech Stack:</span> <span>Svelte, Firebase, Tailwind CSS, and Javascript</span></p>

                    <p><span><span class="text-green-600 font-bold">Description:</span> <span>Website portfolio for web developers and digital marketters.</span></span></p>

                    <p><span class="text-green-600 font-bold">Features:</span> <span>web portfolio for developers and digital marketters.</span></p>

                    <p><span class="text-green-600 font-bold">Live Demo:</span> <a class="underline text-gray-300" target="_blank" href="/">click here</a></p>
                    <!-- <p><span class="text-green-600 font-bold">GitHub Repo:</span> <a class="underline text-gray-300" target="_blank" href="/">click here</a>
                    </p> -->
                </ol>
</div>
        </div>
  
  </section>

  <!-- SKILLS -->
<section id="skills">
    <div class="text-4xl sm:text-5xl md:text-6xl items-center p-8">
        <h1 class="text-center">Tech Skills</h1>

        <div class="flex justify-center items-center h-full w-full text-4xl">
            <svg class="h-8 " xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" viewBox="0 0 24 24">
                <circle cx="18" cy="12" r="0" fill="#78d65c">
                    <animate attributeName="r" begin=".67" calcMode="spline" dur="1.5s" keySplines="0.2 0.2 0.4 0.8;0.2 0.2 0.4 0.8;0.2 0.2 0.4 0.8" repeatCount="indefinite" values="0;2;0;0"/>
                </circle>
                <circle cx="12" cy="12" r="0" fill="#78d65c">
                    <animate attributeName="r" begin=".33" calcMode="spline" dur="1.5s" keySplines="0.2 0.2 0.4 0.8;0.2 0.2 0.4 0.8;0.2 0.2 0.4 0.8" repeatCount="indefinite" values="0;2;0;0"/>
                </circle>
                <circle cx="6" cy="12" r="0" fill="#78d65c">
                    <animate attributeName="r" begin="0" calcMode="spline" dur="1.5s" keySplines="0.2 0.2 0.4 0.8;0.2 0.2 0.4 0.8;0.2 0.2 0.4 0.8" repeatCount="indefinite" values="0;2;0;0"/>
                </circle>
            </svg>
        </div>
        
        <div class="bg-gray-800 text-lg p-3 sm:w-[500px] justify-center item-center sm:mx-auto">
            <span> <span class="ml-4">As</span> a <span class="font-extrabold text-green-600">Full-Stack Web Developer</span>, I specialize in designing and developing modern, high-performance web applications with seamless user experiences. My frontend expertise includes <span class="font-extrabold text-green-600">HTML, CSS, Tailwind CSS, JavaScript, and Svelte.js</span>, allowing me to create visually stunning and responsive interfaces. On the backend, I leverage the <span class="font-extrabold text-green-600">MERN stack (MongoDB, Express.js, React.js, and Node.js)</span> to build scalable and efficient applications.
            <br>
            <span class="ml-4">Additionally</span>, I have experience working with <span class="font-extrabold text-green-600">Firebase</span> for real-time database management, authentication, and cloud functions, making application development faster and more reliable. I also integrate various third-party APIs to enhance application functionality, such as payment gateways, geolocation services, and AI-driven features. I am continuously learning and keeping up with the latest industry trends to build secure, scalable, and innovative digital solutions.</span>
        </div>
    </div>
</section>

<!-- SERVICES -->
<section id="services">

    <div class="text-4xl sm:text-5xl md:text-6xl items-center p-5 w-full h-full">
        <h1 class="text-center">Services I offer</h1>

        <div class="flex justify-center items-center h-full w-full text-4xl">
            <svg class="h-8" xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" viewBox="0 0 24 24">
                <circle cx="18" cy="12" r="0" fill="#78d65c">
                    <animate attributeName="r" begin=".67" calcMode="spline" dur="1.5s" keySplines="0.2 0.2 0.4 0.8;0.2 0.2 0.4 0.8;0.2 0.2 0.4 0.8" repeatCount="indefinite" values="0;2;0;0"/>
                </circle>
                <circle cx="12" cy="12" r="0" fill="#78d65c">
                    <animate attributeName="r" begin=".33" calcMode="spline" dur="1.5s" keySplines="0.2 0.2 0.4 0.8;0.2 0.2 0.4 0.8;0.2 0.2 0.4 0.8" repeatCount="indefinite" values="0;2;0;0"/>
                </circle>
                <circle cx="6" cy="12" r="0" fill="#78d65c">
                    <animate attributeName="r" begin="0" calcMode="spline" dur="1.5s" keySplines="0.2 0.2 0.4 0.8;0.2 0.2 0.4 0.8;0.2 0.2 0.4 0.8" repeatCount="indefinite" values="0;2;0;0"/>
                </circle>
            </svg>
        </div>

    <div class="block p-3 lg:grid lg:grid-cols-3  space-y-4 lg:space-y-11 lg:space-x-4 text-lg">


        <div class="border focus-none border-green-500 shadow-lg shadow-green-500 p-4">

            <p class="text-2xl font-bold text-green-600 text-center">Web Development</p>
            <ol class="mt-6 space-y-5">

                <p><span class="text-green-600 font-bold">Custom Website Design :</span> <span>Build responsive and visually appealing websites tailored to clients' needs.</span></p>

                <p><span><span class="text-green-600 font-bold">Frontend Development :</span> <span>Create modern, fast, and user-friendly interfaces using Svelte, JavaScript, and Tailwind CSS.</span></span></p>

                <p><span class="text-green-600 font-bold">Full-Stack Web Development :</span> <span>Develop both frontend and backend applications using Node.js and Firebase.</span></p>

            </ol>
        </div>


        <div class="border focus-none border-green-500 shadow-lg shadow-green-500 p-4">

            <p class="text-2xl font-bold text-green-600 text-center">UI/UX Design</p>
            <ol class="mt-6 space-y-5">

                <p><span class="text-green-600 font-bold">Responsive Web Design :</span> <span>Ensure websites look great on all devices (mobile, tablet, desktop).
                </span></p>

                <p><span><span class="text-green-600 font-bold">Tailwind CSS Styling :</span> <span>Build beautiful, optimized UI components using Tailwind CSS.
                    User Interface Optimization – Improve site design and interactivity for better user engagement.</span></span></p>

            </ol>
        </div>

        <div class="border focus-none border-green-500 shadow-lg shadow-green-500 p-4">

            <p class="text-2xl font-bold text-green-600 text-center">Web Performance Optimization</p>
            <ol class="mt-6 space-y-5">

                <p><span class="text-green-600 font-bold">Fast & Lightweight Websites :</span> <span>Optimize loading speed and performance using modern best practices.
                </span></p>

                <p><span><span class="text-green-600 font-bold">SEO-Friendly Development :</span> <span>Implement clean code structures to improve search rankings.</span></span></p>

            </ol>
        </div>

        <div class="border focus-none border-green-500 shadow-lg shadow-green-500 p-4">

            <p class="text-2xl font-bold text-green-600 text-center">Web App Development</p>
            <ol class="mt-6 space-y-5">

                <p><span class="text-green-600 font-bold">Svelte & SvelteKit Applications :</span> <span>Develop dynamic, interactive, and scalable applications.</span></p>

                <p><span><span class="text-green-600 font-bold">Firebase Integration :</span> <span>Build serverless apps with authentication, database, and cloud functions.</span></span></p>

            </ol>
        </div>

        <div class="border focus-none border-green-500 shadow-lg shadow-green-500 p-4">

            <p class="text-2xl font-bold text-green-600 text-center">Website Maintenance & Support</p>
            <ol class="mt-6 space-y-5">

                <p><span class="text-green-600 font-bold">Bug Fixing & Debugging :</span> <span>Identify and fix issues in existing projects.</span></p>

                <p><span><span class="text-green-600 font-bold">Code Refactoring :</span> <span> Improve code quality for better maintainability.</span></span></p>

                <p><span class="text-green-600 font-bold">Security Enhancements :</span> <span>Protect websites from vulnerabilities and threats.
                </span></p>

            </ol>
        </div>


        <div class="border focus-none border-green-500 shadow-lg shadow-green-500 p-4">

            <p class="text-2xl font-bold text-green-600 text-center">API Integration & Backend Development</p>
            <ol class="mt-6 space-y-5">

                <p><span class="text-green-600 font-bold">REST API & Firebase Backend :</span> <span>Set up databases, authentication, and serverless functions.</span></p>

                <p><span><span class="text-green-600 font-bold">Payment Gateway Integration :</span> <span>Implement Stripe, PayPal, or other payment solutions.</span></span></p>

            </ol>
        </div>

        <div class="border focus-none border-green-500 shadow-lg shadow-green-500 p-4">

            <p class="text-2xl font-bold text-green-600 text-center">Landing Pages & E-commerce</p>
            <ol class="mt-6 space-y-5">

                <p><span class="text-green-600 font-bold">Custom Landing Pages :</span> <span>Design high-converting pages for businesses, events, or products.</span></p>

                <p><span><span class="text-green-600 font-bold">E-commerce Website Development :</span> <span>Build simple online stores using modern tech.</span></span></p>

            </ol>
        </div>
        </div>

</section>

<!-- CONTACT ME -->
<section id="contact" class="p-8 text-center items-center justify-center mx-auto">
    <div class="text-4xl sm:text-5xl md:text-6xl items-center justify-center mx-auto flex">
        <h1 class="text-center">Contact Me</h1>

        <div class="flex justify-center items-center h-full w-full text-4xl">
            <svg class="h-8 " xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" viewBox="0 0 24 24">
                <circle cx="18" cy="12" r="0" fill="#78d65c">
                    <animate attributeName="r" begin=".67" calcMode="spline" dur="1.5s" keySplines="0.2 0.2 0.4 0.8;0.2 0.2 0.4 0.8;0.2 0.2 0.4 0.8" repeatCount="indefinite" values="0;2;0;0"/>
                </circle>
                <circle cx="12" cy="12" r="0" fill="#78d65c">
                    <animate attributeName="r" begin=".33" calcMode="spline" dur="1.5s" keySplines="0.2 0.2 0.4 0.8;0.2 0.2 0.4 0.8;0.2 0.2 0.4 0.8" repeatCount="indefinite" values="0;2;0;0"/>
                </circle>
                <circle cx="6" cy="12" r="0" fill="#78d65c">
                    <animate attributeName="r" begin="0" calcMode="spline" dur="1.5s" keySplines="0.2 0.2 0.4 0.8;0.2 0.2 0.4 0.8;0.2 0.2 0.4 0.8" repeatCount="indefinite" values="0;2;0;0"/>
                </circle>
            </svg>
        </div>
        <div class="border border-green-500 shadow-lg shadow-green-500 p-4 justify-center items-center mx-auto text-center w-[480px]">

            
            <p class="text-lg text-center">GET IN TOUCH</p>
            
            <div class="sm:flex mt-3 text-lg font-bold text-center items-center justify-center space-x-3">
            
                <!-- email -->
                 <div class="flex">
            
                     <a href="mailto:carmenjosh84@gmail.com" target="_blank" class="hover:text-green-400 text-center flex gap-2 hover:bg-gray-800 p-2 rounded-lg ">
                         <svg xmlns="http://www.w3.org/2000/svg" width="30" height="30" viewBox="0 0 24 24"><g fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"><path stroke-dasharray="64" stroke-dashoffset="64" d="M4 5h16c0.55 0 1 0.45 1 1v12c0 0.55 -0.45 1 -1 1h-16c-0.55 0 -1 -0.45 -1 -1v-12c0 -0.55 0.45 -1 1 -1Z"><animate fill="freeze" attributeName="stroke-dashoffset" dur="0.6s" values="64;0"/></path><path stroke-dasharray="24" stroke-dashoffset="24" d="M3 6.5l9 5.5l9 -5.5"><animate fill="freeze" attributeName="stroke-dashoffset" begin="0.6s" dur="0.2s" values="24;0"/></path></g></svg>
                     E-mail me</a>
                 </div>
            
            <p class="text-lg font-light mt-1 ml-8 text-start sm:text-center">Or</p>
            <!-- telegram -->
             <div class="flex">
            
                 <a href="https://t.me/dipsyjosh" target="_blank" class="hover:text-green-400 flex gap-2 hover:bg-gray-800 p-2 rounded-lg">
                  <svg xmlns="http://www.w3.org/2000/svg" width="30" height="30" viewBox="0 0 24 24"><g fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"><path stroke-dasharray="20" stroke-dashoffset="20" d="M21 5l-2.5 15M21 5l-12 8.5"><animate fill="freeze" attributeName="stroke-dashoffset" dur="0.4s" values="20;0"/></path><path stroke-dasharray="24" stroke-dashoffset="24" d="M21 5l-19 7.5"><animate fill="freeze" attributeName="stroke-dashoffset" dur="0.4s" values="24;0"/></path><path stroke-dasharray="14" stroke-dashoffset="14" d="M18.5 20l-9.5 -6.5"><animate fill="freeze" attributeName="stroke-dashoffset" begin="0.4s" dur="0.3s" values="14;0"/></path><path stroke-dasharray="10" stroke-dashoffset="10" d="M2 12.5l7 1"><animate fill="freeze" attributeName="stroke-dashoffset" begin="0.4s" dur="0.3s" values="10;0"/></path><path stroke-dasharray="8" stroke-dashoffset="8" d="M12 16l-3 3M9 13.5l0 5.5"><animate fill="freeze" attributeName="stroke-dashoffset" begin="0.7s" dur="0.3s" values="8;0"/></path></g></svg>
                 DM me
                 </a>
             </div>
        </div>


</div>
</section>

<!-- PLAYING SONG DIV -->
<div class="fixed top-1/4 right-0 transform -translate-y-1/2 bg-gray-700 text-white p-2 rounded-l-lg shadow-lg flex flex-col space-y-2">
    <button on:click={toggleSound} class="p-4 hover:bg-gray-800 transition">
        {#if isPlaying}
  <!-- Sound On Icon -->
  <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
    <polygon points="3 9 9 9 15 3 15 21 9 15 3 15"></polygon>
    <path d="M17 8a5 5 0 0 1 0 8"></path>
    <path d="M19 5a9 9 0 0 1 0 14"></path>
</svg>
{:else}
<!-- Sound Off Icon -->
<svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
    <polygon points="3 9 9 9 15 3 15 21 9 15 3 15"></polygon>
    <line x1="21" y1="9" x2="21" y2="15"></line>
    <line x1="18" y1="12" x2="24" y2="12"></line>
</svg>
{/if}

    </button>
    </div>


<audio id="audioPlayer" autoplay muted loop>
    <source src="/yvSG60yjYQoz.128.mp3" type="audio/mpeg">
        Your browser does not support the audio element.
</audio> <!-- Hidden audio element -->

 