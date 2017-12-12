---
title: "Visual Studio での Python のクロスプラットフォーム リモート デバッグ | Microsoft Docs"
ms.custom: 
ms.date: 07/12/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa667357-763f-4ce6-8e47-48f9337658a8
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 7d5526bbcde438896f63c0f9b4f75d919d3ca457
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="remotely-debugging-python-code-on-linux"></a>Linux 上の Python コードのリモート デバッグ

Visual Studio は、Windows コンピューター上でローカルまたはリモートで Python アプリケーションを起動およびデバッグすることができます (「[Remote Debugging](../debugger/remote-debugging.md)」(リモート デバッグ) をご覧ください)。 また、別のオペレーティング システム、デバイス、または CPython 以外の Python 実装を [ptvsd ライブラリ](https://pypi.python.org/pypi/ptvsd)を使用してリモートでデバッグすることもできます。

ptvsd を使用する場合、デバッグ対象の Python コードは Visual Studio がアタッチできるデバッグ サーバーをホストします。 このホストには、コードに小さな変更を加えてサーバーをインポートして有効にする必要があります。また、TCP 接続を許可するようにリモート コンピューター上でネットワークまたはファイアウォールを構成する必要が生じる場合があります。

リモート デバッグの概要については、Visual Studio 2015 と 2017 の両方に該当する「[Deep Dive: Cross-Platform Remote Debugging](https://youtu.be/y1Qq7BrV6Cc)」(詳細情報: クロスプラットフォームのリモート デバッグ) (youtube.com、6 分 22 秒) をご覧ください。

> [!VIDEO https://www.youtube.com/embed/y1Qq7BrV6Cc]

## <a name="setting-up-a-linux-computer"></a>Linux コンピューターのセットアップ

このチュートリアルを実行するには、次の項目が必要です。

- Mac OSX や Linux などのオペレーティング システムで Python を実行しているリモート コンピューター。
- そのコンピューターのファイアウォールで開いているポート 5678 (受信)。これはリモート デバッグの既定値です。

[Azure に Linux 仮想マシン](https://docs.microsoft.com/azure/virtual-machines/linux/creation-choices)を簡単に作成し、Windows から[リモート デスクトップを使用してアクセス](https://docs.microsoft.com/azure/virtual-machines/linux/use-remote-desktop)できます。 VM に Ubuntu を使用すると、既定で Python がインストールされるので便利です。Ubuntu を使用しない場合、Python をダウンロードできるその他の場所については、「[Install a Python interpreter of your choice](python-environments.md#selecting-and-installing-python-interpreters)」(好みの Python インタープリターをインストールする) の一覧を参照してください。

Azure VM のファイアウォール ルールの作成方法については、「[Azure Portal を使用した Azure の VM へのポートの開放](https://docs.microsoft.com/azure/virtual-machines/windows/nsg-quickstart-portal)」を参照してください。

## <a name="preparing-the-script-for-debugging"></a>デバッグのためのスクリプトの準備

1. リモート コンピューターで、次のコードを含む `guessing-game.py` という Python ファイルを作成します。

  ```python
  import random

  guesses_made = 0
  name = input('Hello! What is your name?\n')
  number = random.randint(1, 20)
  print('Well, {0}, I am thinking of a number between 1 and 20.'.format(name))

  while guesses_made < 6:
      guess = int(input('Take a guess: '))
      guesses_made += 1
      if guess < number:
          print('Your guess is too low.')
      if guess > number:
          print('Your guess is too high.')
      if guess == number:
          break
  if guess == number:
      print('Good job, {0}! You guessed my number in {1} guesses!'.format(name, guesses_made))
  else:
      print('Nope. The number I was thinking of was {0}'.format(number))
  ```
 
1. `pip3 install ptvsd` を使用して環境に `ptvsd` パッケージをインストールします。 (注: トラブルシューティングが必要な場合に備えて、インストールされている ptvsd のバージョンを記録しておくことをお勧めします。[ptvsd 一覧](https://pypi.python.org/pypi/ptvsd)にも使用できるバージョンが記載されています)。

1. 下のコードを他のコードよりも前の、`guessing-game.py`のできるだけ早い段階で追加して、リモート デバッグを有効にします。 (厳密な要件ではありませんが、`enable_attach` 関数を呼び出す前に起動されたバックグラウンド スレッドをデバッグすることはできません。)

   ```python
   import ptvsd
   ptvsd.enable_attach('my_secret')
   ```

   `enable_attach` に渡される最初の引数 ("シークレット" と呼ばれます) は、実行中のスクリプトへのアクセスを制限します。このシークレットは、リモート デバッガーをアタッチするときに入力します (推奨されませんが、`enable_attach(secret=None)` の接続と使用を任意のユーザーに許可することもできます)。

1. ファイルを保存して `python3 guessing-game.py` を実行します。 `enable_attach` を呼び出すとバックグラウンドで実行され、受信接続を待機します。それ以外の場合はプログラムと対話しています。 必要な場合は、`wait_for_attach` 関数を `enable_attach` の後に呼び出して、デバッガーがアタッチされるまでプログラムをブロックすることもできます。

> [!Tip]
> `enable_attach` と `wait_for_attach` に加えて、ptvsdにはヘルパー関数 `break_into_debugger` も用意されています。この関数は、デバッガーがアタッチされている場合にプログラムのブレークポイントとして機能します。 また、デバッガーがアタッチされている場合に `True` を返す `is_attached` 関数もあります (他の `ptvsd` 関数を呼び出す前にこの結果を確認する必要はありません)。

## <a name="attaching-remotely-from-python-tools"></a>Python Tools からのリモート アタッチ

以下の手順では、リモート プロセスを停止する単純なブレークポイントを設定します。

1. ローカル コンピューターでリモート ファイルのコピーを作成し、Visual Studio で開きます。 ファイルの場所は任意ですが、名前はリモート コンピューターのスクリプト名と一致している必要があります。

1. (省略可能) ローカル コンピューター上の ptvsd 用に IntelliSense を使用するには、ptvsd パッケージを Python 環境にインストールします。

1. **[デバッグ]、[プロセスにアタッチ]** の順に選択します。

1. 表示される **[プロセスにアタッチ]** ダイアログで、**[接続の種類]** を **[Python remote (ptvsd)]** (Python リモート (ptvsd)) に設定します (旧バージョンの Visual Studio では、これらのコマンドは **[トランスポート]**と **[Python リモート デバッグ]** という名称でした)。

1. **[接続先]** フィールド (旧バージョンでは **[修飾子]**) に「`tcp://<secret>@<ip_address>:5678`」と入力します。`<secret>` は Python コードで渡される文字列 `enable_attach` です。`<ip_address>` はリモート コンピューターの IP アドレスです (明示的なアドレスまたは myvm.cloudapp.net のような名前を指定できます)。`:5678` はリモート デバッグ ポート番号です。

    > [!Warning]
    > パブリック インターネット経由で接続している場合は、代わりに `tcps` を使用し、以下の「[デバッガー接続の SSL によるセキュリティ保護](#securing-the-debugger-connection-with-ssl)」の指示に従ってください。

1. Enter キーを押すと、そのコンピューターで使用できる ptvsd プロセスの一覧が生成されます。

    ![接続のターゲットの入力とプロセスの一覧表示](media/remote-debugging-qualifier.png)

    この一覧の生成後にリモート コンピューターで別のプログラムを起動する場合は、**[更新]** ボタンを選択します。

1. プロセスを選択してデバッグし、**[アタッチ]** を選択するか、プロセスをダブルクリックします。

1. Visual Studio はデバッグ モードに切り替わり、スクリプトは引き続きリモート コンピューターで実行され、通常の[デバッグ](debugging.md)機能もすべて使用できます。 たとえば、`if guess < number:` 行のブレークポイントを設定し、リモート コンピューターに切り替え、別の推測を入力します。 その後、ローカル コンピューターの Visual Studio はそのブレークポイントで停止し、ローカル変数などが表示されます。

    ![ブレークポイントにヒットした状態](media/remote-debugging-breakpoint-hit.png)

1. デバッグを停止すると、Visual Studio はプログラムからデタッチされますが、リモート コンピューターでは実行が継続されます。 また、ptvsd もデバッガーのアタッチを引き続きリッスンするので、いつでもプロセスに再アタッチできます。

### <a name="connection-troubleshooting"></a>接続のトラブルシューティング

1. **[接続の種類]** で **[Python remote (ptvsd)]**(Python リモート (ptvsd)) (旧バージョンでは **[トランスポート]** の **[Python remote debugging]**(Python リモート デバッグ)) を選択していることを確認します。
1. **[Connection Target]**(接続のターゲット) (または **[修飾子]**) のシークレットがリモート コードのシークレットと完全に一致することを確認します。
1. **[接続先]** (または **[修飾子]**) の IP アドレスがリモート コンピューターと一致することを確認します。
1. リモート コンピューターのリモート デバッグ ポートを開いていること、接続先に `:5678` などのポート サフィックスを含めていることを確認します。
    - 別のポートを使用する必要がある場合は、`enable_attach` の呼び出しで `ptvsd.enable_attach(secret = 'my_secret', address = ('0.0.0.0', 8080))` のように `address` 引数を使用して指定できます。 この場合、ファイアウォールでもそのポートを開きます。
1. `pip3 list` から返されたリモート コンピューターにインストールされている ptvsd のバージョンが、Visual Studio で使用している Python ツールのバージョンで使用されている ptvsd のバージョン (以下の表を参照してください) が一致することを確認します。 必要に応じて、リモート コンピューターの ptvsd を更新します。

    | Visual Studio のバージョン | Python ツール/ptvsd のバージョン |
    | --- | --- |
    | 2017 15.3 | 3.2.0 |
    | 2017 15.2 | 3.1.0 |
    | 2017 15.0, 15.1 | 3.0.0 |
    | 2015 | 2.2.6 |
    | 2013 | 2.2.2 |
    | 2012, 2010 | 2.1 |


## <a name="securing-the-debugger-connection-with-ssl"></a>デバッガー接続の SSL によるセキュリティ保護

ptvsd のリモート デバッグ サーバーへの接続は、既定で、シークレットのみで保護されており、すべてのデータはプレーンテキストで渡されます。 より高いセキュリティの接続には、ptvsd でサポートされている SSL を使用します。設定手順は次のとおりです。

1. リモート コンピューターで、openssl を使用して別の自己署名証明書とキー ファイルを生成します。
    
    ```bash
    openssl req -new -x509 -days 365 -nodes -out cert.cer -keyout cert.key
    ```

    openssl のプロンプトが表示されたら、**[共通名]** のホスト名または IP アドレス (接続できればどちらでも可) を入力します

    (詳細については、Python `ssl` モジュール ドキュメントの「[Self-signed certificates](http://docs.python.org/3/library/ssl.html#self-signed-certificates)」(自己署名証明書) を参照してください。 これらのドキュメントのコマンドは、1 つの結合されたファイルのみを生成する点に注意してください)。

1. このコードで、`enable_attach` の呼び出しを修正し、値としてファイル名を使用して `certfile` 引数と `keyfile` 引数を含めます (これらの引数の意味は、標準の `ssl.wrap_socket` Python 関数の引数と同じです)。

    ```python
    ptvsd.enable_attach(secret='my_secret', certfile='cert.cer', keyfile='cert.key')
    ```
    
    また、ローカル コンピューターのコード ファイルでも同じ変更を加えることもできます。ただし、このコードは実際には実行されないので、厳密には必要ありません。    

1. リモート コンピューターで Python プログラムを再起動し、デバッグできる状態にします。

1. Visual Studio がインストールされた Windows コンピューターの [信頼されたルート CA] にその証明書を追加して、チャネルをセキュリティで保護します。

    1. リモート コンピューターの証明書ファイルをローカル コンピューターにコピーします。
    1. コントロール パネルを開き、**[管理ツール] > [コンピューター証明書の管理]** に移動します。
    1. 表示されるウィンドウで、左側の **[信頼されたルート証明機関]** を展開し、**[証明書]** を右クリックして **[すべてのタスク] > [インポート]** を選択します。
    1. リモート コンピューターからコピーした `.cer` ファイルに移動して選択し、ダイアログの指示に従ってクリックしてインポートを完了します。

1. 前述の手順で Visual Studio のアタッチ プロセスを繰り返します。今回は、**[Connection Target]**(接続のターゲット) (または **[修飾子]**) として `tcps://` を使用します。

    ![SSL を使用するリモート デバッグ トランスポートの選択](media/remote-debugging-qualifier-ssl.png)

### <a name="warnings"></a>警告

後述のように、Visual Studio で SSL で接続するときに証明書の問題の可能性が表示されます。 この警告を無視して続行しても問題ありません。無視しても、man-in-the-middle 攻撃を受ける可能性がある傍受を防ぐために、チャネルは暗号化されます。

1. 以下の "リモート証明書は信頼されていません" という警告が表示される場合は、[信頼されたルート CA] に証明書が適切に追加されていないことを示します。 追加手順を確認して、もう一度試してください。

    ![SSL 証明書の信頼の警告](media/remote-debugging-ssl-warning.png)

1. 以下の "リモート証明書名がホスト名と一致しません" という警告が表示される場合は、証明書の作成時に **[共通名]** として正しいホスト名または IP アドレスを指定していないことを示します。

    ![SSL 証明書のホスト名の警告](media/remote-debugging-ssl-warning2.png)

> [!Warning]
> 現在、これらの警告を無視すると、Visual Studio 2017 はハングします。 すべての問題を修正してから、接続を試行してください。
