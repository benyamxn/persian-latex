# persian-latex
A Persian Latex Template that can be used in different instances such as assignments, exams, quizzes; Not suitable for long documents such as theses or project reports.

**You can also read `Guide.pdf` file for insructions in Farsi.**

# Features and user guide

## Config
In order to start using the template yourself, open the `config.tex` file and chang the macros accordingly. Do NOT remove the first `%`.
```Latex
\newcommand{\type}{%
% type of the document you want to create (تمرین\کوئیز\میان‌ترم etc.)
}
\newcommand{\myName}{%
% your full name
}
\newcommand{\myStdID}{%
% your student ID
}
\newcommand{\institudeName}{%
% the name of your institude
}
\newcommand{\departmentName}{%
% the name of your department
}
\newcommand{\semester}{%
% ongoing semseter, for example: نیم‌سال اول تحصیلی 00$-$1399
}
\newcommand{\probname}{%
% the term used to represent problems, for example: سؤال\مسئله
}
```
Replace `logo.png` with any other image you want as the logo of your institude. The image format doesn't neccessarily need to be `png`.

To create the main output, you must either use `\header` or `\cover`; Cover is more suitable when you need to physically print your document, otherwise use header. The syntax for both is similar:
```Latex
\header{courseName}
{teacherName}
{hwNumber}
```
For example, assuming you defined `\type` as `تمرین`, the output for
```Latex
\header{معماری}
{دکتر بیات}
{اول}
```
will look something like:

![alt text](https://raw.githubusercontent.com/benyamxn/persian-latex/main/images/header.png "How header looks like")


Make sure you have the fonts installed. They can be found in the `Fonts` folder; You can also change them at the end of `configs.tex` to have your own fonts.

It is adviced to have `Template.tex` stay as unoccupied as possible. Let `main.tex` be where you type most of your code.
It is also highly recommended to change `./` at the beginning of `Template.tex` into the absolute path of where you saved the template; By doing so you will only need to copy `Template.tex` file and create a new `main.tex` file. Otherwise you need to copy the entire template anytime you want to use it.

## Features and how to use them
I have implemented environments to type problems, solutions, proofs and even environments with arbitrary names. All have appropiate visual properties which I'll explain in their own section.

### Typing a problem
Use `prob` environment to write the problem description (or solution) for your document:
```Latex
\begin{prob}
	% problem
\end{prob}
```
The document will automatically start enumerating the problems, starting at 1; The number of your problem increases each time you use the `prob` environment.
You can also have a problem with your desired number by using `probnum`:
```Latex
\begin{probnum}{--num--}
	% a problem with number --num--
\end{probnum}
```
Of course problem numbers will keep increasing, following the number you type. Here's how `prob` looks like:

![alt text](https://raw.githubusercontent.com/benyamxn/persian-latex/main/images/prob.png "Example of prob environment")



### Typing a solution
You can by all means use `prob` just to type the solution of the problem; But in case you wanted to have both problem description and its solution, you just need to use `sol` environment after the problem:
```Latex
\begin{sol}
	% problem
\end{sol}
```
At the end of `sol`, a black square is added at the end of the final line to indicate the end of the solution. Here's how it looks like:

![alt text](https://raw.githubusercontent.com/benyamxn/persian-latex/main/images/sol.png "Example of sol environment")

### Typing an environment with custom name
Sometimes you might feel the need to have a section of your solution to have a statement as claim, lemma etc. You can use `customEnv` to have a statement labeled by your desired name; The body of the environment will have italic text. By default, `customEnv` won't have a counter for your environment. You can instead use `customEnvnum` to have multiple instances of a custom environment.
```Latex
\begin{customEnv}{envName}
	% an environment labeled by envName
\end{customEnv}

\begin{customEnvnum}{envName}{envNum}
	% an environment labeled by envName numbered by envNum
\end{customEnvnum}
```
The environment will look like this:

![alt text](https://raw.githubusercontent.com/benyamxn/persian-latex/main/images/customEnv.png "Example of custom environment")

### Typing a proof
Each custom environment most likely needs a proof after itself. I have a `proof` environment implemented for this reason:
```Latex
\beign{proof}
  % proof for a statement
\end{proof}
```
`proof` environment will look like this:

![alt text](https://raw.githubusercontent.com/benyamxn/persian-latex/main/images/proof.png "Example of proof environment")

### Mathematical Macros
I've added some macros to help typing mathemathical equations in some particular cases. Read `mathemathical_macros.pdf` to see the use cases.
