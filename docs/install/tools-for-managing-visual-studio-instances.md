---
title: "Visual Studio インスタンスの検出および管理用のツール | Microsoft Docs"
description: "{{プレースホルダー}}"
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
ms.assetid: 85686707-14C0-4860-9B7A-66485D43D241
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
ms.openlocfilehash: a6c3aa65a2c0198c856f09f6f16f58bf16945d58
ms.contentlocale: ja-jp
ms.lasthandoff: 05/09/2017

---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Visual Studio インスタンスの検出および管理用のツール

## <a name="detecting-existing-visual-studio-instances"></a>既存の Visual Studio インスタンスの検出
クライアント コンピューターにインストールされている Visual Studio インスタンスを検出して管理するために役立つ複数のツールが用意されています。

* [VSWhere](https://github.com/microsoft/vswhere): Visual Studio のインストール済みインスタンスから主要な Visual Studio ツールの場所を見つけるために役立つ、C++ の実行可能ファイルです。
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell): セットアップ構成 API を使用して Visual Studio のインストール済みインスタンスを識別する PowerShell スクリプトです。
* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples): セットアップ構成 API を使用して既存のインストールを照会する方法を示す C# と C++ のサンプルです。

さらに、[セットアップ構成 API](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.setup.configuration.aspx) は、Visual Studio インスタンスを問い合わせるために独自のユーティリティを構築する開発者向けのインターフェイスを提供します。

>[!TIP]
>Visual Studio 2017 のインストールの詳細については、[Heath Stewart のブログ記事](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/)を参照してください。


## <a name="editing-the-registry-for-a-visual-studio-instance"></a>Visual Studio インスタンスのレジストリの編集
Visual Studio 2017 ではレジストリ設定はプライベートな場所に保存されているため、同じバージョンの Visual Studio の複数のインスタンスを side-by-side で同じコンピューターで使用できます。

これらのエントリはグローバル レジストリには保存されないため、レジストリ エディターを使用してレジストリ設定を変更するための特別な指示があります。

1. Visual Studio 2017 で開いているインスタンスがある場合は、閉じてください。
2. `regedit.exe` を起動します。
3. `HKEY_LOCAL_MACHINE` ノードを選択します。
4. レジストリ エディターのメイン メニューから **[ファイル] -> [ハイブの読み込み...]** を選択して、**AppData\Local** フォルダーに保存されているプライベート レジストリ ファイルを選択します。 例:
   ```
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

> [!NOTE]
> `<config>` は参照する Visual Studio のインスタンスに対応します。

分離されたハイブの名前になるハイブ名を指定するように求められます。 これを行うと、作成した分離されたハイブの下にあるレジストリを参照できるようになります。

> [!IMPORTANT]
> Visual Studio を再度開始する前に、作成した分離されたハイブをアップロードする必要があります。 これを行うには、レジストリ エディターのメイン メニューから [ファイル] -> [ハイブのアンロード] を選択します。 (これを行わない場合、ファイルがロックされたままになり、Visual Studio で開始することができません。)

