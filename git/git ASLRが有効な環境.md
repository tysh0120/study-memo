ASLRが有効なWindowsにインストールする場合
/AddmandatoryASLRsecurityexceptions=Enabled オプションを付けてインストーラーを起動する

> Git-2.49.0-64-bit.exe /AddmandatoryASLRsecurityexceptions=Enabled

ASLRの設定は、「Windowsセキュリティ」　アプリとブラウザーコントロール > Exploit protection > イメージのランダム化を強制する（必須ASLR)

上記オプションはgitの例外設定を登録してくれる