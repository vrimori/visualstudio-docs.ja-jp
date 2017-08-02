---
title: "R Tools for Visual Studio のインストール | Microsoft Docs"
ms.custom: 
ms.date: 4/28/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ff60292-1b88-4ee9-b2b2-edd957f1a519
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 90b2481b0ec4f9387fe3a2c0b733a103e8c03845
ms.openlocfilehash: bc0b1112fe6f3acf2605101a863d831f41bb5f6d
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017

---

# <a name="how-to-install-r-tools-for-visual-studio"></a>R Tools for Visual Studio のインストール方法

このトピックの内容

- [サポートされている Visual Studio のバージョン](#supported-versions-of-visual-studio)
- [Visual Studio 2017 での RTVS のインストール](#installing-rtvs-in-visual-studio-2017)
- [Visual Studio 2015 での RTVS のインストール](#installing-rtvs-in-visual-studio-2015)
- [オフライン インストール](#offline-installation-of-visual-studio-and-rtvs)

> [!Note]
> R Tools をインストールすると、「[オプション](options.md#data-scientist-layout)」トピックで説明したように、最適化されたデータ科学レイアウト用に Visual Studio を構成できます。

## <a name="supported-versions-of-visual-studio"></a>サポートされている Visual Studio のバージョン

R Tools for Visual Studio (RTVS) は、[Visual Studio 2015 Update 3 (以降)](http://go.microsoft.com/fwlink/?LinkId=691129) および [Visual Studio 2017](https://www.visualstudio.com/downloads/) の Community、Professional、および Enterprise の各エディションでサポートされています。 

Visual Studio Test Professional や SQL Server Management Studio などの他の製品に含まれている Visual Studio Shell しかない場合、RTVS はインストールされません。 これは、Visual Studio Shell に RTVS に必要なコンポーネントがないためです。


## <a name="installing-rtvs-in-visual-studio-2017"></a>Visual Studio 2017 での RTVS のインストール

> [!Important]
> Windows 7 の Visual Studio 2017 での RTVS のインストールは、[GitHub の問題 #3561](https://github.com/Microsoft/RTVS/issues/3561) で説明されているように、現在ブロックされています。 これは、Visual Studio 2017 の 15.3 アップデートで解決される予定です。

1. Visual Studio インストーラーを実行します。
2. [**データ サイエンスと分析のアプリケーション**] ワークロードを選択します。

    ![VS2017 の [データ サイエンスと分析のアプリケーション] ワークロード](~/docs/rtvs/media/installation-data-science-workload.png)

3. 同じワークロード名で、右側にその他のオプションを設定します。 既定では、このワークロードには F# と Python のサポートが含まれていることに注意してください。 R の場合、少なくとも [**R 言語サポート**]、[**R 開発ツールのランタイム サポート**]、および [**Microsoft R クライアント**] を選択する必要があります。

RTVS は次の場所にインストールされます。 `%ProgramFiles(x86)%\Microsoft Visual Studio\<version>\<edition>Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio` ここで、`<version>` は、通常 `2017` で、`<edition>` は `Community`、`Professional`、または `Enterprise` です。

## <a name="installing-rtvs-in-visual-studio-2015"></a>Visual Studio 2015 での RTVS のインストール

Visual Studio 2015 では、R インタープリターと R Tools を個別にインストールする必要があります。

### <a name="install-an-r-interpreter"></a>R インタープリターをインストールする

RTVS には、次の 1 つ以上のソースから R 3.2.1 以降のバージョンの 64 ビット版のインストールが必要です。

* [Microsoft R Open](https://mran.microsoft.com/download/)
* [Microsoft R Client](https://msdn.microsoft.com/microsoft-r/r-client-get-started)
* [CRAN R](https://cran.r-project.org/bin/windows/base/)

Microsoft R Open と CRAN R はどちらも複数の side-by-side バージョンを許可しています。 ただし、Microsoft R Client は、1 つのバージョンのみをサポートし、インストールされている最新バージョンを常に使用します。

### <a name="install-the-r-tools"></a>R Tools のインストール

[https://aka.ms/rtvs-current](https://aka.ms/rtvs-current) から最新の RTVS をダウンロードします。 RTVS は Visual Studio の適切なバージョンを確認し、R インタープリターがまだインストールされていない場合は、インストールの支援も行います。

RTVS は次の場所にインストールされます。`%ProgramFiles(x86)%\Microsoft Visual Studio 14\Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`

## <a name="offline-installation-of-visual-studio-and-rtvs"></a>Visual Studio と RTVS のオフライン インストール

オフライン インストールは、インターネットに接続されていないコンピューターに適しています。

1. 次の指示に従って、お使いの Visual Studio のバージョンのオフライン インストーラーを作成します。 

    - [Visual Studio 2017](../install/create-an-offline-installation-of-visual-studio.md)
    - [Visual Studio 2015](https://msdn.microsoft.com/library/mt706497.aspx)

1. オフライン インストーラーから Visual Studio をインストールします。
1. [RTVS をダウンロード](https://aka.ms/rtvs-current)し、通常どおりにインストールします。

## <a name="see-also"></a>関連項目

- [R の概要](getting-started-with-r.md)
- [R Tools のサンプル プロジェクト](getting-started-samples.md)
- [ヘルプ情報の入手](getting-started-help.md)
- [オプションの設定](options.md)

