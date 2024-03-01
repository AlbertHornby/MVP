class Model:
    def __init__(self):
        self.username = ''
        self.password = ''

    def set_credentials(self, username, password):
        self.username = username
        self.password = password

    def authenticate(self):
        if self.username == 'admin' and self.password == 'password':
            return True
        else:
            return False


class View:
    def display_message(self, message):
        print(message)

    def get_input(self, prompt):
        return input(prompt)

    def show_login_screen(self):
        print("Welcome to the login screen.")
        username = self.get_input("Enter your username: ")
        password = self.get_input("Enter your password: ")
        return username, password


class Presenter:
    def __init__(self, model, view):
        self.model = model
        self.view = view

    def login(self):
        self.view.display_message("Please log in.")
        username, password = self.view.show_login_screen()
        self.model.set_credentials(username, password)
        if self.model.authenticate():
            self.view.display_message("Login successful.")
        else:
            self.view.display_message("Login failed. Please try again.")


# 示例用法
model = Model()
view = View()
presenter = Presenter(model, view)
presenter.login()
