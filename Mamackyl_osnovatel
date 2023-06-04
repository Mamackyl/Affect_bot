import telebot
import cv2
import os
from telebot import types
import urllib.request
bot = telebot.TeleBot("6166748046:AAEkkA6bTi_uYcIktkfm0JmzHYkeeF-6JR8")
@bot.message_handler(commands = ["start"])
def start (m, res = False):
    bot.send_message(m.chat.id, 'Нажми: \nОтправьте фото ')
@bot.message_handler(content_types=['photo'])
def handle_photo(message):
    IMG_DIR = 'C:/Users/segua/PycharmProjects/pythonProject31'
    img_path = os.path.join(IMG_DIR, "1" + '.jpg')
    urllib.request.urlretrieve(bot.get_file_url(message.photo[-1].file_id), img_path)
    markup = types.ReplyKeyboardMarkup(resize_keyboard=True)
    item1 = types.KeyboardButton("/Ч/б")
    item2 = types.KeyboardButton("/Блюр")
    item3 = types.KeyboardButton("/Странный")
    item4 = types.KeyboardButton("/Квадрат")
    markup.add(item1)
    markup.add(item2)
    markup.add(item3)
    markup.add(item4)
    bot.send_message(message.chat.id, 'Нажми: \nВыберите эффект ', reply_markup=markup)
@bot.message_handler(commands=["Ч/б"])
def handle_text(message):
    bot.send_message(message.chat.id, 'Идет обработка' )
    image = cv2.imread("C:/Users/segua/PycharmProjects/pythonProject31/1.jpg")
    gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
    cv2.imwrite("C:/Users/segua/PycharmProjects/pythonProject31/1.jpg", gray)
    with open("C:/Users/segua/PycharmProjects/pythonProject31/1.jpg",'rb') as photo:
        bot.send_message(message.chat.id, "Все готово")
        bot.send_photo(message.chat.id,photo)
@bot.message_handler(commands=["Блюр"])
def handle_text(message):
    bot.send_message(message.chat.id, ' Идет обработка' )
    image = cv2.imread("C:/Users/segua/PycharmProjects/pythonProject31/1.jpg")
    blurred = cv2.GaussianBlur(image, (51, 51), 0)
    cv2.imwrite("C:/Users/segua/PycharmProjects/pythonProject31/1.jpg", blurred)
    with open("C:/Users/segua/PycharmProjects/pythonProject31/1.jpg",'rb') as photo:
        bot.send_message(message.chat.id, "Все готово")
        bot.send_photo(message.chat.id,photo)
@bot.message_handler(commands=["Странный"])
def handle_text(message):
    bot.send_message(message.chat.id, 'Идет обработка ' )
    image = cv2.imread("C:/Users/segua/PycharmProjects/pythonProject31/1.jpg")
    ret, threshold_image = cv2.threshold(image, 127, 255, 0)
    cv2.imwrite("C:/Users/segua/PycharmProjects/pythonProject31/1.jpg", threshold_image )
    with open("C:/Users/segua/PycharmProjects/pythonProject31/1.jpg", 'rb') as photo:
        bot.send_message(message.chat.id, "Все готово")
        bot.send_photo(message.chat.id, photo)
@bot.message_handler(commands=["Квадрат"])
def handle_text(message):
    bot.send_message(message.chat.id, 'Идет обработка ' )
    image = cv2.imread("C:/Users/segua/PycharmProjects/pythonProject31/1.jpg")
    scale_percent = 20  # Процент от изначального размера
    width = int(image.shape[1] * scale_percent / 100)
    height = int(image.shape[0] * scale_percent / 100)
    dim = (width, height)
    resized = cv2.resize(image, dim, interpolation=cv2.INTER_AREA)
    cv2.imwrite("C:/Users/segua/PycharmProjects/pythonProject31/1.jpg", resized )
    with open("C:/Users/segua/PycharmProjects/pythonProject31/1.jpg", 'rb') as photo:
        bot.send_message(message.chat.id, "Все готово")
        bot.send_photo(message.chat.id, photo)
bot.polling(none_stop=True, interval=0)
