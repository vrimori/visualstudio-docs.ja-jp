---
title: "ユニバーサル Windows プラットフォーム (UWP) 向けアプリの開発 | Microsoft Docs"
ms.custom: 
ms.date: 10/24/2017
ms.reviewer: 
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eac59cb6-f12e-4a77-9953-6d62b164a643
caps.latest.revision: "48"
author: stevehoag
ms.author: shoag
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: a696a0b827cc8fe367390efbba01c2a18ff178bb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="develop-apps-for-the-universal-windows-platform-uwp"></a>ユニバーサル Windows プラットフォーム (UWP) 向けアプリの開発
ユニバーサル Windows プラットフォームと 1 つの Windows コアを使用することで、電話やデスクトップなどの Windows 10 デバイスで同じアプリを実行できます。 これらのユニバーサル Windows アプリは、Visual Studio とユニバーサル Windows アプリ開発ツールを使用して作成します。  
  
 ![ユニバーサル Windows プラットフォーム](../cross-platform/media/uwp_coreextensions.png "UWP_CoreExtensions")  
  
 アプリを Windows 10 Phone、Windows 10 デスクトップ、または Xbox で実行します。 同じアプリ パッケージが使用されています。 Windows 10 の単一の統一されたコアの導入により、1 つのアプリケーション パッケージをすべてのプラットフォームで実行できます。 いくつかのプラットフォームには、プラットフォーム固有の動作を利用するためにアプリに追加できる拡張 SDK があります。 たとえば、モバイル用の拡張 SDK を使用すれば、Windows Phone で [戻る] ボタンを処理できます。 プロジェクトで拡張 SDK を参照する場合、単純にランタイム チェックを追加して、プラットフォームでその SDK を使用できるかどうかをテストします。 このようにして、それぞれのプラットフォームで同じアプリ パッケージを使用できます。  
  
 **Windows のコアとは何ですか。**  
  
 Windows では初めて、すべての Windows 10 プラットフォームで共通のコアを持つようリファクタリングされました。 1 つの共有ソース、1 つの共通 Windows カーネル、1 つのファイル I/O スタック、および 1 つのアプリ モデルがあります。 UI については、1 つの XAML UI フレームワークと、1 つの HTML UI フレームワークしかありません。 さまざまな Windows 10 デバイス上でアプリを簡単に実行できるようになっているため、優れたアプリの作成に集中できます。  
  
 **ユニバーサル Windows プラットフォームとは何ですか。**  
  
ユニバーサル Windows プラットフォームとは、簡単にいえば、コントラクトとバージョンのコレクションです。 これらにより、アプリを実行する対象となる場所を指定できます。 オペレーティング システムを対象にすることはなくなり、1 つまたは複数のデバイス ファミリを対象にするようになります。 詳しくは、「[ユニバーサル Windows プラットフォームの紹介](/windows/uwp/get-started/universal-application-platform-guide)」をご覧ください。  
  
## <a name="requirements"></a>必要条件  
 ユニバーサル Windows アプリの開発ツールには、別のデバイス上のアプリの外観を確認する際に使用できるエミュレーターが付属しています。 これらのエミュレーターを使用する場合は、このソフトウェアを物理マシンにインストールする必要があります。 その物理マシンでは、Windows 8.1 (x64) Professional エディション以上が実行され、クライアント Hyper-V および第 2 レベルのアドレス変換 (SLAT) をサポートするプロセッサが搭載されている必要があります。 Visual Studio が仮想マシンにインストールされている場合は、エミュレーターを使用できません。  
  
 必要なソフトウェアの一覧を次に示します。  
  
-   [Windows 10](http://windows.microsoft.com/windows/downloads)。 Visual Studio 2017 は、Windows 10 でのみ UWP の開発をサポートします。 詳しくは、Visual Studio の「[対象となるプラットフォーム](https://www.visualstudio.com/productinfo/vs2017-compatibility-vs)」および「[システム要件](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs)」をご覧ください。   
  
-   [Visual Studio](https://www.visualstudio.com/downloads/)。 オプションのユニバーサル Windows プラットフォーム開発ワークロードも必要です。  

     ![UWP ワークロード](media/uwp_workload.png)
  
このソフトウェアをインストールしたら、開発用に Windows 10 デバイスを有効にする必要があります。 「[デバイスを開発用に有効にする](/windows/uwp/get-started/enable-your-device-for-development)」をご覧ください。 Windows 10 デバイスごとに開発者ライセンスは必要ありません。  
    
## <a name="universal-windows-apps"></a>ユニバーサル Windows アプリ  
希望する開発言語を C#、Visual Basic、C++ または JavaScript の中から選び、Windows 10 デバイスを対象とするユニバーサル Windows プラットフォーム アプリを作成します。 「[最初のアプリの作成](/windows/uwp/get-started/your-first-app)」またはビデオ「[Tools for Windows 10 Overview](http://channel9.msdn.com/Series/ConnectOn-Demand/229)」(Windows 10 用ツールの概要) をご覧ください。
  
既存の Windows 8.1 のストア アプリ、Windows Phone 8.1 アプリ、または Visual Studio 2015 で作成されたユニバーサル Windows アプリがある場合、最新のユニバーサル Windows プラットフォームを使用するよう、これらのアプリを移植する必要があります。 「[Windows ランタイム 8.x から UWP への移行](/windows/uwp/porting/w8x-to-uwp-root)」をご覧ください。
  
ユニバーサル Windows アプリを作成したら、アプリをパッケージ化して、それを Windows 10 デバイスにインストールするか Windows ストアに送信する必要があります。 「[アプリのパッケージ化](/windows/uwp/packaging/index)」をご覧ください。

## <a name="see-also"></a>関連項目
[Visual Studio におけるクロス プラットフォーム モバイル開発](../cross-platform/cross-platform-mobile-development-in-visual-studio.md)  
