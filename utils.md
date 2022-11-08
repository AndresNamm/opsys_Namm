+ Create .venv
~~~
python3 -m venv .venv
~~~
+ Install grip 
~~~
pip install grip
~~~
+ Convert md to html with grip
~~~
grip praks12_azurejawsl.md --export praks12_azurejawsl.pdf
~~~
+ Convert html to pdf with pandoc.
~~~
pandoc praks12_azurejawsl.html -t latex -o t.pdf
~~~