import requests  

TOKEN = "507725219:DkB9rUm7XHi9aiEKNVPCjqPDrpLzk54yeD5tRRzU"  # توکن ربات خودت رو جایگزین کن  
API_URL = f"https://tapi.bale.ai/bot{TOKEN}/"

def get_updates():
    url = API_URL + "getUpdates"
        response = requests.get(url)
            return response.json()

            def send_message(chat_id, text):
                url = API_URL + "sendMessage"
                    data = {"chat_id": chat_id, "text": text}
                        requests.post(url, json=data)

                        def main():
                            last_update_id = 0
                                while True:
                                        updates = get_updates()
                                                if updates["ok"]:
                                                            for update in updates["result"]:
                                                                            update_id = update["update_id"]
                                                                                            if update_id > last_update_id:
                                                                                                                last_update_id = update_id
                                                                                                                                    chat_id = update["message"]["chat"]["id"]
                                                                                                                                                        text = update["message"]["text"]
                                                                                                                                                                            send_message(chat_id, f"شما گفتید: {text}")

                                                                                                                                                                            if __name__ == "__main__":
                                                                                                                                                                                main()