This project is documenting the process of me learning how to use TailwindCSS. I hope it helps someone else at some point. One of the biggest challenges for me in getting started with coding was getting a grasp on the development tools that are needed. I hope this can also be a help to anyone who is new to setting up tools for development or new to the tools that have been used for this project. 

I will at some point also add the instructions for setting up npm and npx. I ran into some problems and I hope that will be helpful to someone else who is new to those tools like I am. 

I am using git for version control. I will likely only show the commands I'm using for the project. I will add resources to help get git started on your machine. 

**FYI: Things You Don't Necessarily Need**

I use VIM and Atom text editors currently. If you want to learn <a href="https://danielmiessler.com/study/vim/">VIM</a> here's something that can help. 

I also use <a href="https://www.hamvocke.com/blog/a-quick-and-easy-guide-to-tmux/"	>tmux</a> so I can split my terminal panes and quickly switch back and forth. Here a <a href="https://tmuxcheatsheet.com/">cheat sheet</a> if you're interested. 

If you are not comfortable with VIM or tmux, just use whatever text editor you are comfortable to edit files. You can either use the terminal or whatever other way you are comfortable with to create new files when that's needed.


I will be using the terminal to do certain things. If you are new using the terminal/CLI(Command Line Interface) <a href="https://learnrubythehardway.org/book/appendixa.html">here is a good resource to learn from</a>. For now you can use the same commands I do. I'm using a version of Ubuntu so when I want to paste into the terminal I have to use **Ctrl+Shift+V** and if I wanted to copy from the terminal it would be **Ctrl+Shift+C**

**Installing npm**
COMING SOON (I hope)

**Getting Started With Tailwind**

I first made a directory to hold my project. I named my project folder simplePage, you can name yours something else. If you're new to programming you might want to keep the same name simply so it's one less thing to think about for now. 

```
mkdir simplePage && cd simplepage
```

I initiated a git repository:

```
git init 
```


Here is Tailwinds documentation as a reference. Here is the page with <a href="https://tailwindcss.com/docs/installation">instructions for installing Tailwind via npm</a>

But I ended up first following along with their <a href="https://www.youtube.com/watch?v=qYgogv4R8zg&list=PL5f_mz_zU5eXWYDXHUDOLBE0scnuJofO0&index=2">video that covers this also</a>.

I'll create an index.html file first:

```
vi index.html

```

This both creates to file and opens it up in the terminal for me to edit. 

Start with this boilerplace code in the file:

```HTML
<!-- index.html --> 
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
     <title>Page Title</title>
     <link rel="stylesheet" href="/css/tailwind.css">
  </head>
  
  <body>
 	<h1>Hello World</h1>
 </body>
 
 
 </html>

```

ADDED LINK TO tailwind.css BEFORE CREATING THE FOLDER/FILE

The video also gives an example of how to get Tailwind into your file using CDN, I won't show that right now. 

Next I will create a folder to hold CSS files and then create a Tailwind CSS file in that folder.

```
mkdir css
vi css/tailwind.css
```

We will add a few things to the css file we just created that are needed for using Tailwind.

```CSS
/* tailwind.css */
@tailwind base;
@tailwind components;
@tailwind utilities;

```

**Options For Frontend Setup**
If you already use a different framework like Vue, React, or Laravel, you can <a href="https://tailwindcss.com/docs/installation">find instructions</a> for setting that up on the Tailwind website. 

Vite is a front end development tool that I found pretty simple to get started with. 

**Setting Up**

In the terminal run:
```
npm init -y
```


Next, we will install some necessary packages into our dev dependencies (hence the -D). We install Tailwind, PostCSS, Autoprefixer, and Vite:

```
npm install -D tailwindcss postcss autoprefixer vite
```

Open the `package.json` file and make and edit in the `"scripts"` section.
Find this line:

```
"scripts": {
       "test": "echo \"Error: no test specified\" && exit 1"
     },

```


And change it to this:

```
"scripts": {
       "dev": "vite"  
     },
```

This runs Vite and starts our Dev server. 


**Configure Tailwind & PostCSS**

Run this in the terminal (The `-p` flag runs the PostCSS configuration):

```
npx tailwindcss init -p
```


You should see something like this output in your terminal:

```
tailwindcss 2.1.1
  
   ??? Created Tailwind config file: tailwind.config.js
   ??? Created PostCSS config file: postcss.config.js

```

As you can see, two new files were created for us. 

We can use the Tailwind Config file to extend and customize things.


And now we can run our server:

```
npm run dev
```


You should see an output in your terminal similar to this:

```
  vite v2.1.5 dev server running at:

  > Local:    http://localhost:3000/
  > Network:  http://192.168.0.11:3000/

  ready in 337ms.


```

Open `http://localhost:3000` in your browser and have a look.<br>
*NOTE* If you see errors in your terminal or your web page check for any useful info from the errors. Especially be on the lookout for typos. It won't be as forgiving about missing bits like HTML by itself may be. 

The Vite server will automatically refresh the page if we make a change in our files. To check this out you can try changing to the text in the `h1` tag in the `index.html` file. 

As an example here is one thing I did:

```
<h1 class="text-red-600">Hello World</h1>
```

That will change the color to a shade of red, feel free to try different number 

For more info on how to use colors in Tailwind you can <a href="https://tailwindcss.com/docs/customizing-colors"> visit here</a>.

Here is some info about Tailwinds<a href="https://tailwindcss.com/docs/preflight"> base styles</a> along with some code snippets you can try inserting in your code to try out. Feel free to do that now to get a feel for some things. 


***FOR FUTURE REFERENCE: Tailwind cli build command (different from in video)***
```
npx tailwindcss-cli@latest build css/tailwind.css -o build/tailwind.css
```