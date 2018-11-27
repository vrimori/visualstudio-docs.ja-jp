---
title: '方法: Visual Studio の特定のリリースのインストール |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- install a specific release, Visual Studio
ms.assetid: d69ad0f8-f0a0-438e-a0ef-777c4868f139
caps.latest.revision: 20
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: e25c7e47b1d80cbdf30304ed3f4e6568704bb3d7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792828"
---
# <a name="how-to-install-a-specific-release-of-visual-studio"></a>方法: Visual Studio の特定のリリースをインストールする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

最新で最適化されたバージョンのオプション機能をご利用いただけるよう、Visual Studio のセットアップは頻繁に更新されています。  しかし、以前のリリースの Visual Studio 2015 (たとえば、iOS サポートが含まれている Update 1 より前のリリースの Visual Studio 2015) をインストールする場合は、Visual Studio セットアップで強制的に以前のバージョンのフィーチャー マニフェスト ファイルを使用する必要があります。 この記事では、その方法について説明します。  
  
## <a name="installing-the-current-release"></a>現在のリリースのインストール  
 Visual Studio 2015 の最初のリリースから変更を加えましたセットアップ エンジンとマニフェスト ファイル何回か。  つまりから web インストーラーをダウンロードする場合、 [Visual Studio のダウンロード](https://www.visualstudio.com/downloads/download-visual-studio-vs)クリーンでインターネットに接続されたマシンでの web サイトは、インストールをセットアップする最新の Visual Studio 2015 の更新、最新の製品の機能強化が含まれます省略可能な機能とツールの更新も、最近のバージョン。  
  
## <a name="installing-earlier-releases"></a>以前のリリースのインストール  
 作成し、ISO イメージをマウント、またはダウンロードして、インストーラーから直接起動[My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015)を .exe ファイルを追加のコマンド ライン パラメーターを追加します (/custominstallpath、//InstallSelectableItems、/NoRestart など)。Visual Studio をインストールする方法を制御します。  
  
 次の表には、特定の時点のシナリオと Enterprise edition のインストーラーに渡す必要があります、ために必要なコマンド ライン パラメーターが含まれています。 (同じパラメーターは、Community または Professional エディションのインストーラーでも機能します)。  
  
|Visual Studio 2015 エディション|実行対象|使用するコマンド ライン|セットアップの機能|  
|--------------------------------|-----------------|--------------------------|---------------------|  
|Visual Studio Enterprise (最新の公開リリース)|更新プログラムを visual Studio Enterprise (から使用可能な[My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015))|`vs_enterprise.exe` **注:** このインストールの既定の動作は、最新の省略可能な機能を提供し、そのため、必要がないコマンド ライン パラメーターです。|Visual Studio セットアップでは、最新の feed.xml が使われ、最新のファイルがインストールされます|  
|Visual Studio Enterprise Update 3 (さらに更新プログラム 3 の時代 (年号) 更新がなくても元の更新プログラム 3)|Visual Studio Enterprise RTM ( [MSDN サブスクリプションのダウンロード ページ](https://msdn.microsoft.com/subscriptions/downloads/)から入手可能)|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/6/B/B/6BBD3561-D764-4F39-AB8E-05356A122545/20160628.2/enu/feed.xml`|Visual Studio のセットアップが更新プログラム 3 がリリースされたときに利用可能だった feed.xml を使用してください。|  
|Visual Studio Enterprise の Update 2 の (元は、更新プログラム 2、ただし、更新プログラムを事前に最新の更新プログラム 3)|Visual Studio Enterprise RTM ( [MSDN サブスクリプションのダウンロード ページ](https://msdn.microsoft.com/subscriptions/downloads/)から入手可能)|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/6/B/B/6BBD3561-D764-4F39-AB8E-05356A122545/20160620.2/enu/feed.xml`|Visual Studio のセットアップが更新プログラム 3 をリリースする前に最新だった feed.xml を使用してください。|  
|Visual Studio Enterprise (さらに更新プログラム 2 の時代 (年号) 更新がなくても元の Update 2)|Visual Studio Enterprise RTM ( [MSDN サブスクリプションのダウンロード ページ](https://msdn.microsoft.com/subscriptions/downloads/)から入手可能)|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/0/6/B/06BB0C5C-C767-4250-91DA-AB463377597E/20160405.3/enu/feed.xml`|Visual Studio のセットアップが更新プログラム 2 がリリースされたときに利用可能だった feed.xml を使用してください。|  
|Visual Studio Enterprise の Update 1 の (元は、更新プログラム 1 が、更新プログラムを事前に最新の更新プログラム 2)|Visual Studio Enterprise RTM ( [MSDN サブスクリプションのダウンロード ページ](https://msdn.microsoft.com/subscriptions/downloads/)から入手可能)|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20160225.3/enu/feed.xml`|Visual Studio のセットアップが更新プログラム 2 をリリースする前に最新だった feed.xml を使用してください。|  
|Visual Studio Enterprise Update 1 (Update 1 になってからの更新プログラムを何も含んでいない、オリジナルの Update 1)|Visual Studio Enterprise RTM ( [MSDN サブスクリプションのダウンロード ページ](https://msdn.microsoft.com/subscriptions/downloads/)から入手可能)|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20151201.1/enu/feed.xml`|Visual Studio セットアップでは、Update 1 がリリースされたときに利用可能だった feed.xml を使用します。|  
|Visual Studio Enterprise (オリジナルの RTM ではあるものの、Update 1 より前の更新プログラムを持つもの)|Visual Studio Enterprise RTM (  [MSDN サブスクリプションのダウンロード ページ](https://msdn.microsoft.com/en-us/subscriptions/downloads/)から入手可能)|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/6/1/36188D5F-479F-4A46-BF55-6AE5928D1EBB/20151102.3/enu/feed.xml`|Visual Studio セットアップでは、Update 1 がリリースされるまで最新だった feed.xml を使用します。|  
|Visual Studio Enterprise (更新プログラムのないオリジナルの RTM)|Visual Studio Enterprise RTM ( [MSDN サブスクリプションのダウンロード ページ](https://msdn.microsoft.com/subscriptions/downloads/)から入手可能)|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/5/7/B/57BF5016-E4F0-4EB5-BE27-2BFA87E7723F/20150713.1/enu/feed.xml`|Visual Studio セットアップでは、RTM がリリースされたときに利用可能だった feed.xml を使用します。|  
  
> [!IMPORTANT]
>  使用する言語によって、"enu" (英語) を次の値のいずれかに置き換えてください。  
> 
> - chs (簡体字中国語)  
>   -   cht (繁体字中国語)  
>   -   csy (チェコ語)  
>   -   deu (ドイツ語)  
>   -   esn (スペイン語)  
>   -   fra (フランス語)  
>   -   ita (イタリア語)  
>   -   jpa (日本語)  
>   -   kor (韓国語)  
>   -   plk (ポーランド語)  
>   -   ptb (ポルトガル語)  
>   -   rus (ロシア語)  
>   -   trk (トルコ語)  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio 管理者ガイド](../install/visual-studio-administrator-guide.md)