from kivy.app import App
from kivy.uix.gridlayout import GridLayout
from kivy.uix.button import Button
from kivy.uix.textinput import TextInput

class CalculatorApp(App):
    def build(self):
        self.operator = None
        self.last_was_operator = None
        self.last_button = None
        layout = GridLayout(cols=4)
        self.result = TextInput(multiline=False, readonly=True, halign="right", font_size=30)
        layout.add_widget(self.result)
        buttons = [
            '7', '8', '9', '/',
            '4', '5', '6', '*',
            '1', '2', '3', '-',
            'C', '0','+'
        ]
        for button in buttons:
            button_widget = Button(text=button, pos_hint={'center_x': 1, 'center_y': 1})
            button_widget.bind(on_press=self.on_button_click)
            layout.add_widget(button_widget)
        equals_button = Button(text="=", pos_hint={'center_x': 1, 'center_y': 1})
        equals_button.bind(on_press=self.on_solution)
        layout.add_widget(equals_button)

        return layout

    def on_button_click(self, instance):
        current = self.result.text
        button_text = instance.text

        if button_text == 'C':
            self.result.text = ""
        else:
            new_text = current + button_text
            self.result.text = new_text

    def on_solution(self, instance):
        text = self.result.text
        try:
            solution = str(eval(self.result.text))
            self.result.text = solution
        except Exception:
            self.result.text = "Ошибка."

if __name__ == "__main__":
    app = CalculatorApp()
    app.run()
