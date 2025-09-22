# test
sddasdasfasvda
asasf
wdawdawdaw
dawdawd

qawda
wd
awd
# webhook_demo.py
from flask import Flask, request

app = Flask(__name__)

@app.route("/github-webhook", methods=["POST"])
def github_webhook():
    data = request.json
    event = request.headers.get("X-GitHub-Event")

    if event == "push":
        branch = data["ref"].split("/")[-1]
        pusher = data["pusher"]["name"]
        print(f"🔔 收到推送！分支：{branch}  作者：{pusher}")
    elif event == "ping":
        print("✅ GitHub 连通测试通过")
    return "OK", 200

if __name__ == "__main__":
    app.run(port=8000)