---
title: "低帯域幅または信頼性の低いネットワーク環境にインストールする | Microsoft Docs"
description: "信頼性の低いネットワーク環境における Visual Studio インストーラーの動作とインストールの開始前にインストール ファイルをダウンロードする方法について説明します。"
ms.date: 04/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 44DB1998-68CD-4560-870A-EE5B993DCF6E
author: timsneath
ms.author: tims
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 9dbe70bce6c246416df64de304b06cd211320f2a
ms.contentlocale: ja-jp
ms.lasthandoff: 05/09/2017

---

# <a name="install-visual-studio-2017-on-low-bandwidth-or-unreliable-network-environments"></a>低帯域幅または信頼性の低いネットワーク環境に Visual Studio 2017 をインストールする
Visual Studio 2017 インストーラーは、さまざまなネットワーク環境またはさまざまなコンピューター環境で問題なく動作するように設計されています。

- Visual Studio のインストールに必要なファイルはグローバル配信ネットワークで配信されます。そのため、ローカル サーバーから届けられます。
- インストール プロセス中、アンチウイルス/プロキシ ソフトウェアによる干渉を最小限に抑えるために、3 つの異なるダウンロード技術 (WebClient、BITS、WinInet) が試されます。
- 新しいワークロード ベース モデルでは、旧バージョンの Visual Studio よりインストール回数が少なくなります。

そのため、新しい Web インストーラーを推奨しています。その利便性を実感していただけるものと考えております。 しかしながら、インストール ファイルが正しくダウンロードされたことを確認してから Visual Studio のインストールを始めるのであれば、それも可能です。 コマンド ラインを利用して必要なファイルのローカル キャッシュを作成してからインストールを開始できます。

ここではその方法を説明します。

## <a name="download-the-visual-studio-bootstrapper"></a>Visual Studio ブートストラップをダウンロードする
最初に、選択したエディションの Visual Studio の Visual Studio ブートストラップをダウンロードします。

セットアップ ファイル&mdash; (具体的にはブートストラップ ファイル)&mdash; は、次のいずれかになります (あるいは同様のファイル)。

| エディション                    | ファイル                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio コミュニティ    | [vs_community.exe](https://aka.ms/vs/15/release/vs_community.exe)       |
| Visual Studio Professional | [vs_professional.exe](https://aka.ms/vs/15/release/vs_professional.exe) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/15/release/vs_enterprise.exe)     |

## <a name="create-a-local-install-cache"></a>ローカル インストール キャッシュを作成する
ローカル レイアウトを作成するには、コマンド プロンプトを開き、次の例にあるいずれかのコマンドを使用します。 この例では、Visual Studio Community ブートストラップをダウンロードしているものと想定しています。ご利用のエディションに合わせ、コマンドを適宜調整してください。

- .NET Web と .NET デスクトップ開発の場合、次を実行します。
  ```
  vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
  ```
- .NET デスクトップと Office 開発の場合、次を実行します。
  ```
  vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US
  ```
- C++ デスクトップ開発の場合、次を実行します。
  ```
  vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US
  ```

- すべての機能を備えた完全ローカル レイアウトを作成するには (これには時間がかかりますが、_たくさん_の機能があります)、次を実行します。
  ```
  vs_community.exe --layout c:\vs2017layout --lang en-US
  ```

英語以外の言語をインストールする場合、このページの下の一覧にあるロケールに `en-US` を変更します。 この[利用できるコンポーネントとワークロードの一覧](workload-and-component-ids.md)を利用し、必要に応じて、インストール キャッシュをさらにカスタマイズできます。

## <a name="install-from-the-local-cache"></a>ローカル キャッシュからインストールする
ローカル インストール キャッシュから実行するとき、各ファイルのローカル バージョンを使用します。 ただし、インストール中、キャッシュにないコンポーネントを選択すると、インターネットからのダウンロードが試行されます。

ダウンロードしたファイルのみがインストールされるように、レイアウト キャッシュの作成に利用したものと同じコマンド ライン オプションを使用します。 たとえば、次のコマンドでレイアウト キャッシュを作成した場合、

```
vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
```

このコマンドを利用してインストールを実行します。

```
c:\vs2017layout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional
```

## <a name="list-of-language-locales"></a>言語ロケールの一覧
| **言語ロケール** | **言語** |
| ----------------------- | --------------- |  
| cs-CZ | チェコ語 |
| de-DE | ドイツ語 |
| en-US | 英語 |
| es-ES | スペイン語 |
| fr-FR | フランス語 |
| it-IT | イタリア語 |
| ja-JP | 日本語 |
| ko-KR | 韓国語 |
| pl-PL | ポーランド語 |
| pt-BR | ポルトガル語 - ブラジル |
| ru-RU | ロシア語 |
| tr-TR | トルコ語 |
| zh-CN | 中国語 - 簡体字 |
| zh-TW | 中国語 - 繁体字 |

## <a name="see-also"></a>関連項目
* [Visual Studio のインストール](install-visual-studio.md)
* [Visual Studio 管理者ガイド](visual-studio-administrator-guide.md)
* [コマンド ライン パラメーターを使用して Visual Studio をインストールする](use-command-line-parameters-to-install-visual-studio.md)

