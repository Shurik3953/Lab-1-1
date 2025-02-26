import requests

def get_quote():
    response = requests.get("https://api.quotable.io/random")
    if response.status_code == 200:
        data = response.json()
        quote = data["content"]
        print("Отримана цитата:", quote)
        with open("quote.txt", "w", encoding="utf-8") as file:
            file.write(quote)
    else:
        print("Помилка отримання цитати")

def count_words(filename):
    try:
        with open(filename, "r", encoding="utf-8") as file:
            text = file.read()
            words = text.split()
            print(f"Кількість слів у файлі '{filename}':", len(words))
    except FileNotFoundError:
        print("Файл не знайдено.")

get_quote()
count_words("quote.txt")
