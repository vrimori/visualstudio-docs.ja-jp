---
title: "方法: Visual Studio の特定のリリースをインストールする | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "特定のリリースの Visual Studio をインストールします。"
ms.assetid: d69ad0f8-f0a0-438e-a0ef-777c4868f139
caps.latest.revision: 20
caps.handback.revision: 11
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# 方法: Visual Studio の特定のリリースをインストールする
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

最新で最適化されたバージョンのオプション機能をご利用いただけるよう、Visual Studio のセットアップは頻繁に更新されています。  しかし、以前のリリースの Visual Studio 2015 \(たとえば、iOS サポートが含まれている Update 1 より前のリリースの Visual Studio 2015\) をインストールする場合は、Visual Studio セットアップで強制的に以前のバージョンのフィーチャー マニフェスト ファイルを使用する必要があります。 この記事では、その方法について説明します。  
  
## 現在のリリースのインストール  
 Visual Studio 2015 の最初のリリース以降、セットアップ エンジンは 1 回、マニフェスト ファイルは 6 回以上更新されました。  つまり、インターネットに接続されたクリーンなコンピューターで[今、Visual Studio セットアップをダウンロードして実行](https://www.visualstudio.com/downloads/download-visual-studio-vs)すると、セットアップによって Visual Studio 2015 Update 1 がインストールされます。これには、最新の製品の改善と、最近のより新しいバージョンのオプション機能やツールが含まれます。  
  
## 以前のリリースのインストール  
 ISO イメージを作成してマウントするか、Web インストーラーを直接ダウンロードして実行してから追加のコマンド ライン パラメーター \(\/CustomInstallPath, \/Full, \/InstallSelectableItems, \/NoRestart など\) によって .exe ファイルを追加することにより、 Visual Studio をインストールする方法を制御します。  
  
 次の表に、特定の時点のシナリオと、Enterprise エディションの Web インストーラーに渡す必要のあるコマンド ライン パラメーターを示します。 \(同じパラメーターは、Community または Professional エディションの Web インストーラーでも機能します。\)  
  
|Visual Studio 2015 エディション|実行対象|使用するコマンド ライン|セットアップの機能|  
|-------------------------------|----------|------------------|---------------|  
|Visual Studio Enterprise \(最新の公開リリース\)|Visual Studio Enterprise with Update 1 \([VisualStudio.com](https://www.visualstudio.com/en-us/products/vs-2015-product-editions.aspx) から入手可能\)|`vs_enterprise.exe` **Note:**  このインストールの既定の動作では、最新のオプション機能が提供されるため、コマンド ライン パラメーターは必要ありません。|Visual Studio セットアップでは、最新の feed.xml が使われ、最新のファイルがインストールされます|  
|Visual Studio Enterprise \(オリジナルの RTM ではあるものの、Update 1 より前の更新プログラムを持つもの\)|Visual Studio Enterprise RTM \([MSDN サブスクリプションのダウンロード ページ](https://msdn.microsoft.com/en-us/subscriptions/downloads/)から入手可能\)|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/6/1/36188D5F-479F-4A46-BF55-6AE5928D1EBB/20151102.3/enu/feed.xml`|Visual Studio セットアップでは、Update 1 がリリースされるまで最新だった feed.xml を使用します。|  
|Visual Studio Enterprise Update 1 \(Update 1 になってからの更新プログラムを何も含んでいない、オリジナルの Update 1\)|Visual Studio Enterprise with Update 1 \([MSDN サブスクリプションのダウンロード ページ](https://msdn.microsoft.com/en-us/subscriptions/downloads/)から入手可能\)|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20151201.1/enu/feed.xml`|Visual Studio セットアップでは、Update 1 で利用可能だった feed.xml を使用します。|  
|Visual Studio Enterprise \(更新プログラムのないオリジナルの RTM\)|Visual Studio Enterprise RTM \([MSDN サブスクリプションのダウンロード ページ](https://msdn.microsoft.com/en-us/subscriptions/downloads/)から入手可能\)|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/5/7/B/57BF5016-E4F0-4EB5-BE27-2BFA87E7723F/20150713.1/enu/feed.xml`|Visual Studio セットアップでは、RTM で利用可能だった feed.xml を使用します。|  
  
> [!IMPORTANT]
>  使用する言語によって、"enu" \(英語\) を次の値のいずれかに置き換えてください。  
>   
>  -   chs \(簡体字中国語\)  
> -   cht \(繁体字中国語\)  
> -   csy \(チェコ語\)  
> -   deu \(ドイツ語\)  
> -   esn \(スペイン語\)  
> -   fra \(フランス語\)  
> -   ita \(イタリア語\)  
> -   jpa \(日本語\)  
> -   kor \(韓国語\)  
> -   plk \(ポーランド語\)  
> -   ptb \(ポルトガル語\)  
> -   rus \(ロシア語\)  
> -   trk \(トルコ語\)  
  
## 参照  
 [Visual Studio のインストール](../Topic/Installing%20Visual%20Studio%202015.md)