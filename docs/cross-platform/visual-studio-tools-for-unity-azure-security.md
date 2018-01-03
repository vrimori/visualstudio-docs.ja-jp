---
title: "Visual Studio Tools for Unity と Azure のチュートリアル、セキュリティ | Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: F4FD6E1C-EA64-4613-BDDE-6E4E5CCF983E
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 1ffb0c57329a8453208978cee69daa771d8ee0e9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="update-unity-mono-security-certificate-store"></a>Unity Mono セキュリティ証明書ストアを更新する

Unity Mono に付属する証明書ストアは空であり、いかなるサイトも信頼しません。 詳細については、[Mono セキュリティ FAQ](http://www.mono-project.com/docs/faq/security/) をご覧ください。

TLS / SSL を無視せずに Azure に接続するために、Unity Mono 証明書ストアを更新する必要があります。

## <a name="using-mozroots-to-install-certificates"></a>mozroots を使用して証明書をインストールする

mozroots ツールは Mono に含まれています。 Mozilla のルート証明書一覧がダウンロードされ、インストールされます。

1. コマンド プロンプト ターミナルを開きます。

2. このターミナルで **C:\Program Files\Unity\Editor\Data\MonoBleedingEdge\bin>** ディレクトリに移動します。 実際のパスは、ローカル コンピューターに Unity をインストールした場所によって決まります。

3. 次のコマンドを入力し、**Enter** キーを押して実行します。

  `mono ..\lib\mono\4.5\mozroots.exe --sync --import`

4. 出力は次のようになります (付加される数字や証明書は異なる場合があります)。

  ```
  Downloading from 'https://hg.mozilla.org/releases/mozilla-release/raw-file/default/security/nss/lib/ckfw/builtins/certdata.txt'...
  Importing certificates into user store...
  1 new root certificates were added to your trust store.
  Import process completed.
  ```

5. これで TLS 関連のエラーを受け取らずにサンプル プロジェクトを実行できるはずです。

## <a name="next-step"></a>次のステップ

* [クライアント接続をテストする](visual-studio-tools-for-unity-azure-connection.md)
