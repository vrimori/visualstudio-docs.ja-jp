---
title: "Python Tools for Visual Studio を使用したクロスプラットフォーム リモート デバッグ | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa667357-763f-4ce6-8e47-48f9337658a8
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 7d726441c2d6953bd7b50451bec7fff05d5d71b0
ms.openlocfilehash: 7634da4bdc2b0186f410acb4eaf57a70ddea3e91
ms.lasthandoff: 03/10/2017

---

# <a name="remotely-debugging-python-code"></a>Python コードのリモート デバッグ

Python Tools for Visual Studio (PTVS) は、Windows コンピューター上でローカルまたはリモートで Python アプリケーションを起動およびデバッグすることができます (「[Remote Debugging](../debugger/remote-debugging.md)」(リモート デバッグ) をご覧ください)。 また、別のオペレーティング システム、デバイス、または CPython 以外の Python 実装を [ptvsd ライブラリ](https://pypi.python.org/pypi/ptvsd)を使用してリモートでデバッグすることもできます。

ptvsd を使用する場合、デバッグ対象の Python コードは Visual Studio がアタッチできるデバッグ サーバーをホストします。 そのためには、コードに小さな変更を加えてサーバーをインポートして有効にする必要があります。また、TCP 接続を許可するようにリモート コンピューター上でネットワークまたはファイアウォールを構成する必要が生じる場合があります。

リモート デバッグの概要については、「[Deep Dive: Cross-Platform Remote Debugging](https://youtu.be/y1Qq7BrV6Cc)」(詳細情報: クロスプラットフォームのリモート デバッグ) (youtube.com、6 分 22 秒) をご覧ください。

> [!VIDEO https://www.youtube.com/embed/y1Qq7BrV6Cc]

## <a name="preparing-the-script-for-debugging"></a>デバッグのためのスクリプトの準備

1. リモート コンピューターで、次のコードを含む Python ファイルを作成します。

  ```python
  import random

  guesses_made = 0
  name = raw_input('Hello! What is your name?\n')
  number = random.randint(1, 20)
  print 'Well, {0}, I am thinking of a number between 1 and 20.'.format(name)

  while guesses_made < 6:
      guess = int(raw_input('Take a guess: '))
      guesses_made += 1
      if guess < number:
          print 'Your guess is too low.'
      if guess > number:
          print 'Your guess is too high.'
      if guess == number:
          break
  if guess == number:
      print 'Good job, {0}! You guessed my number in {1} guesses!'.format(name, guesses_made)
  else:
      print 'Nope. The number I was thinking of was {0}'.format(number)
  ```
 
1. `pip install ptvsd` を使用して環境に `ptvsd` パッケージをインストールします。

1. 下のコードを他のコードよりも前の、スクリプトのできるだけ早い段階で追加して、リモート デバッグを有効にします。 (厳密な要件ではありませんが、`enable_attach` 関数を呼び出す前に起動されたバッググラウンド スレッドをデバッグすることはできません。)

   ```python
   import ptvsd
   ptvsd.enable_attach(secret='my_secret')
   ```

   `enable_attach` に渡される `secret` パラメーターは、実行中のスクリプトへのアクセスを制限するために使用します。 アタッチするときに、このパラメーターを Visual Studio で指定する必要があります。指定しない場合は接続が拒否されます。 これを無効にしてすべてのユーザーに接続を許可するには、`enable_attach(secret=None)` を使用します。

1. ファイルを保存し、リモート コンピューターでスクリプトを起動します。 `enable_attach` の呼び出しはバックグラウンドで実行され、着信接続を待機します。 必要な場合は、`wait_for_attach` 関数を `enable_attach` の後に呼び出して、デバッガーがアタッチされるまでプログラムをブロックすることもできます。

`enable_attach` と `wait_for_attach` に加えて、ptvsdにはヘルパー関数 `break_into_debugger` も用意されています。この関数は、デバッガーがアタッチされている場合にプログラムのブレークポイントとして機能します。 また、デバッガーがアタッチされている場合に `True` を返す `is_attached` 関数もあります (他の `ptvsd` 関数を呼び出す前にこの結果を確認する必要はありません)。

## <a name="attaching-remotely-from-python-tools"></a>Python Tools からのリモート アタッチ

以下の手順では、リモート プロセスを停止する単純なブレークポイントを設定します。

1. ローカル コンピューターでリモート ファイルのコピーを作成し、Visual Studio で開きます。 ファイルの場所は任意ですが、名前はアタッチ先となるリモート コンピューターのスクリプト名と一致している必要があります。

1. **[デバッグ] > [プロセスにアタッチ]** を選択して、[プロセスにアタッチ] ダイアログを開きます。

1. **[トランスポート]** を **[Python remote debugging (Python リモート デバッグ)]** に設定します。

1. **[修飾子]** フィールドにリモート コンピューターのアドレスを入力し、Enter キーを押します。 そのコンピューター上の使用可能なプロセスが一覧表示されます。

![修飾子の入力とプロセスの一覧表示](media/remote-debugging-qualifier.png)

1. この段階でのエラーは通常、シークレットが一致しなかった、`ptvsd` のバージョンが PTVS で使用されているバージョンと一致していない、または接続を確立できなかったことを示します。 接続失敗の一般的な原因の 1 つは、リモート コンピューターにデバッグ サーバーのポート (既定では 5678) をブロックするファイアウォールが構成されていることです。 その場合はファイアウォールを再構成するか、別のポートを使用します。別のポートを使用するには、次に示すように `enable_attach` の呼び出しで `address` パラメーターにポートを明示的に指定します。

  ```python
  ptvsd.enable_attach(secret = 'my_secret', address = ('0.0.0.0', 8080))
  ```

  アドレスの形式は、標準の Python モジュール ソケットで `AF_INET` タイプのソケットに対して使用する形式と同じです。詳細については、[ドキュメント](http://docs.python.org/3/library/socket.html#socket-families)をご覧ください。 

1. プロセスが一覧に表示されたら、ダブルクリックしてアタッチします。 スクリプトを続行したまま、Visual Studio でデバッグ ツールが起動します。 上のスクリプトの例では、数値を入力するとブレークポイントにヒットします。

    ![ブレークポイントにヒットした状態](media/remote-debugging-breakpoint-hit.png)

1. この時点で、通常のすべての PTVS デバッグ機能を使用できます。 

1. デバッグを停止すると、Visual Studio がスクリプトからデタッチされますが、スクリプトはリモート コンピューター上で続行されます。 デバッグ サーバーもバッググラウンド スレッドで続行されるため、後で同じ手順を使用してプロセスに再アタッチすることができます。


## <a name="securing-the-debugger-connection-with-ssl"></a>デバッガー接続の SSL によるセキュリティ保護

既定では、PTVS のリモート デバッグ サーバーはセキュリティ保護されません。つまり、シークレットを知っているすべてのユーザーが接続でき、すべてのデータはプレーンテキストで渡されます。 その結果、ネットワーク上の他のユーザーがデータを覗き見たり、さらには man-in-the-middle (MITM) 攻撃を実行したりするおそれが生じます。 これを防ぐため、セキュリティ保護されていないネットワークまたはインターネット経由でデバッグする場合にデバッグ サーバーで SSL がサポートされます。 

チャネルを SSL でセキュリティ保護するには、SSL 証明書が必要です。 [Python 標準モジュールのドキュメント`ssl`](http://docs.python.org/3/library/ssl.html#self-signed-certificates)の説明に従って、自己署名証明書を自分で生成できます。 また、MITM 攻撃を防ぐために、生成した証明書を PTVS を実行している Windows コンピューターの CA のルート ストアに追加する必要があります。 これには証明書マネージャー (certmgr.msc) を使用します。方法については、「[How do I export certificates and/or private keys?](https://answers.microsoft.com/en-us/windows/forum/windows_10-security/how-do-i-export-certificates-andor-private-keys/7722900a-e848-4076-bc50-9e2f5e3c66ac)」(証明書と秘密キーのエクスポート方法を教えてください。) をご覧ください。 なお、インポートには別の証明書ファイル (秘密キーと合わせて&1; つのファイルになっていないもの) が必要になります。 

証明書と秘密キーのファイルを生成して登録したら、それらを使用するようにスクリプト内の `enable_attach` の呼び出しを更新する必要があります。 これには `certfile` および `keyfile` パラメーターを使用します。これらのパラメーターは標準の Python 関数 `ssl.wrap_socket` の場合と同じ意味を持ちます。 たとえば、証明書ファイルの名前が `my_cert.cer` でキー ファイルの名前が `my_cert.key` の場合、次のように使用します。 

```python
ptvsd.enable_attach(secret='my_secret', certfile='my_cert.cer', keyfile='my_cert.key')
```

アタッチ プロセスは前に説明したプロセスとまったく同じですが、[修飾子] で `tcp://` の代わりに `tcps://` という形式を使用します。 

![SSL を使用するリモート デバッグ トランスポートの選択](media/remote-debugging-qualifier-ssl.png)

CA のルート ストアに証明書を追加しなかった場合は、警告メッセージが表示されます。 

![SSL 証明書の警告](media/remote-debugging-ssl-warning.png)

この警告を無視してデバッグを続行することもできます。無視した場合でもチャネルは傍受されないように暗号化されますが、MITM 攻撃を受けるおそれが生じます。

