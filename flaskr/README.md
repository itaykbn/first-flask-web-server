***static
**style.css
*contains the style of the base.html master page


*** __init__

** create_app
*creates the app and configures it
*sets secret_key(for securety)
*links to database 
*loading configuration
*registers bluebrint of the authentication 
*returns the app


*** auth

** bp = Blueprint('auth', __name__, url_prefix='/auth')
*the blueprint of the authentication(gives every method with decoration its qualities)

** register()
*request from the form the username and password
*validates if the input is not empty(will not allow registration in case of true)
*validates against DB to see if already exsit(will not allow registration)
*if all validations correct
1)generates password hash for password
2)inserts username the encrypted password to the DB and forwards to login
*if validations incorrect will flash an error message that will ask the client to resubmit his input

** login()
*request from the form the username and password
*validates if the input is not empty(will not allow log in)
*validates against DB to see if already exsit(will not allow log in in case of false)
*if all validations correct
1)will clear the current session
2)insert the new user's id into the session and forwards to index
*if validations incorrect will flash an error message that will ask the client to resubmit his input

** load_logged_in_user()
*checks if the session is empty.
1) if true will continue to login and regestration
2) if false will log in automaticlly

** logout()
*clears the session and redirects to index

** login_required(view)
*if user is loaded it continues normally, if not then it redirect to the login page 


*** blog
** no docomentation


*** db

** get_db()
*connects to the splite3 db servise and configures it as the current's app 'DATABASE'
*tells the row_factory to return only rows that behave like dicts(allows accesing collums by name)


** close_db(e=None):
*gets the db from the 'g' object and checks if its not none(to validate that the db really exists)
*closes the flow to the db if the above statmet is true

**init_db()
*gets the db and opens the schema.sql as a file and reads it

** init_db_command()
*creats a new terminal command that is called init-db
*it calls init db and when done prints 'initialized the database'

** init_app(app)
*creats a teardown_appcontext(tells flask to call this when cleaning up after response) which is the close_db method
*creats the new command by calling init_id_command method with the click command 'init-db'


***schema.sql
*contains the tables that are required for the project
*more docs will come later

***tamplets/
** base.html - is the "master page" of all the other web pages in this folder
**auth
*login.html - login html page (master page -base.html)
*register.html - registertion html page (master page -base.html)



----notes----











 