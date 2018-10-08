---
title: 'PTVS の概要: Visual Studio のセットアップ | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec491c1d-bdb2-4c2b-a390-bd808cec635a
caps.latest.revision: 6
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 839ecf84f04d8c1d50b51afb160c14b2a015b6c7
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "47593239"
---
# <a name="getting-started-with-ptvs-setting-up-visual-studio"></a>PTVS の概要: Visual Studio のセットアップ

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

PTVS と関連するライブラリのインストールは、Visual Studio がある場合は簡単です。 Visual Studio がない場合は、プロの品質のバージョンの無償コピーを取得できます。

これらの手順は、非常に短い [youtube ビデオ](https://www.youtube.com/watch?v=_okUV47eM5c&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=1)で視聴できます。
  
高レベルの手順は次のとおり: Visual Studio のインストール、PTVS をインストール、Python とデータ ライブラリ (Anaconda、Canopy) をインストールし、最後に、インストールを確認します。
  
最初に必要なものでは、Visual Studio です。 オープン ソースまたは個人の開発者がいる場合は、Visual Studio を使用することができます[Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs)、無料およびプロフェッショナル向けの機能であります。 クラスルーム学習、学術研究、またはオープン ソース プロジェクトに貢献するはその限りは、組織内 Community Edition を使用することもできます。 学生や新規事業者は DreamSpark と BizSpark プログラムを調べて、無料アクセスの条件を満たしているかを確認するか、または MSDN サブスクリプションがあるかを雇用主に確認してくのださい。
  
Visual Studio をインストールした後に、[PTVS をインストールする](http://pytools.codeplex.com/wikipage?title=PTVS%20Installation)必要があります。 これは、Microsoft によってフルサポートされ、コミュニティの支援を得てオープンに開発された、無料のスタンドアロン拡張です。
  
次に、[Python をインストールする](https://www.python.org/download/)必要があります。 Python は、コミュニティによって管理され、そのホーム ページは python.org。Continuum Analytics Python と多くの便利なライブラリ (特に、サイエンスおよびデータの処理) を持つ Anaconda と呼ばれる無料のバンドルの生成し、Enthought Canopy をという名前のようなバンドルを生成します。 のみ、これらの製品のいずれかをインストールする必要があります。 どちらにするか迷う場合には、最新の Python とインストール困難なパッケージのほとんどを提供する [Anaconda](https://www.continuum.io/downloads) から始めてください。
  
Visual Studio を起動して、すべてが動作していることを確認します。 [表示] メニューで、[その他のウィンドウ] を選択します。 Python Environments という項目があります。 このウィンドウには、PTVS が検出したすべての Python インストール環境と、インストールしたすべてのパッケージが表示されます。 ウィンドウは、コードを編集する際に入力候補を表示するための、データベースの更新も制御します。 この更新プロセスは、時間がかかりますが、完了すると PTVS がパッケージに関するより有用な情報を表示できます。
  
IPython を PTVS と共に使用する場合、これらの[手順](http://pytools.codeplex.com/wikipage?title=Using%20IPython%20with%20PTVS)に従ってください。
  
これらの手順を簡単に見ることができます[youtube ビデオ](https://www.youtube.com/watch?v=_okUV47eM5c&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=1)します。
  
## <a name="see-also"></a>関連項目  

[PTVS の概要と詳細に関するビデオ](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
