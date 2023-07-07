from pyrogram import Client
from pyrogram.raw import functions,types
from threading import Thread 
from pyrogram.errors import UsernameNotOccupied
import time,requests
from datetime import datetime
app = Client("admin",api_id=9212418,api_hash="d783f8ce3d816448d29c4cc2258f838a")


def run_bot():
    app.start()
    print("Bot Started")
    idle()
    print("Bot Stopped")
    app.stop()


admin = input("Enter Admin UserName : @")#يوزرك
g = input("Enter Target UserName : @")
while True:
        url = f"https://t.me/{g}"
        req = requests.get(url)
        if req.text.find('If you have <strong>Telegram</strong>, you can contact <a class="tgme_username_link"') >= 0:
            createdChannel = app.create_channel(title="User")
            ids = createdChannel.id
            app.set_chat_username(ids, g)
            now = datetime.now()
            date = current_time = now.strftime("%H:%M:%S")
            time.sleep(5)
            app.send_message(ids, f"⌥ Done Swap .\n⌥ UserName : @{g}\n⌥ Data : {date}\n⌥ Swap by : @{admin}")
        else:
            req.text.find('Send Message <a class="tgme_action_button_new"') >= 0
            print(f'@{g}')

Thread(target=asyncio.run, args=run_bot).start()

Thread(target=asyncio.run, args=run_bot).start()
