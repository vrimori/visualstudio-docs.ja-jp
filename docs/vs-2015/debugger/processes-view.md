---
title: プロセス ビュー |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.externaltools.spyplus.processesview
helpviewer_keywords:
- Processes view
ms.assetid: e144e70e-eef2-45a7-a562-a177f177d9a1
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c83b57ade3a78a4dcc926e34547ee566326e129
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538360"
---
# <a name="processes-view"></a>プロセス ビュー
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[プロセス ビュー](https://docs.microsoft.com/visualstudio/debugger/processes-view)します。  
  
プロセス ビューには、システム上のすべてのアクティブなプロセスのツリーが表示されます。 プロセス ID とモジュール名が表示されます。 通常、実行中のプログラムに対応する特定のシステム プロセスを確認する場合は、プロセス ビューを使用します。 プロセスは、モジュール名で識別されますまたは「システム プロセスです」を指定します。  
  
 Microsoft Windows では、複数のプロセスをサポートします。 各プロセスは、1 つまたは複数のスレッドを持つことができ、各スレッドは、いずれかを指定できます。 または関連付けられている複数の最上位レベルのウィンドウ。 各最上位ウィンドウには、一連のウィンドウを所有できます。 A + 記号は、レベルが折りたたまれていることを示します。 折りたたまれたビューは、プロセスごとに 1 行で構成されます。 をクリックして、+ 記号レベルを展開します。  
  
 通常、実行中のプログラムに対応する特定のシステム プロセスを確認する場合は、プロセス ビューを使用します。 プロセスは、モジュール名で識別されますまたは「システム プロセスです」を指定します。 プロセスを検索するには、ツリーを折りたたむし、一覧を検索します。  
  
## <a name="procedures"></a>手順  
  
#### <a name="to-open-the-processes-view"></a>プロセス ビューを開く  
  
1.  **スパイ**] メニューの [選択**プロセス**します。  
  
 ![Spy&#43; &#43;プロセス ビュー](../debugger/media/spy-processes.png "スパイ + _Processes")  
Spy++ プロセス ビュー  
  
 上記の図は、展開プロセスとスレッドのノードを持つプロセス ビューを示しています。  
  
### <a name="in-this-section"></a>このセクションの内容  
 [プロセス ビューでプロセスの検索](../debugger/how-to-search-for-a-process-in-processes-view.md)  
 プロセス ビューで、特定のプロセスを検索する方法について説明します。  
  
 [プロセスのプロパティを表示します。](../debugger/how-to-display-process-properties.md)  
 メッセージに関する詳細情報を表示する方法について説明します。  
  
### <a name="related-sections"></a>関連項目  
 [Spy++ ビュー](../debugger/spy-increment-views.md)  
 Windows、メッセージ、プロセス、およびスレッドの spy++ ツリー ビューについて説明します。  
  
 [Spy++ の使用](../debugger/using-spy-increment.md)  
 Spy++ ツールを紹介し、使用方法について説明します。  
  
 [[プロセス検索] ダイアログ ボックス](../debugger/process-search-dialog-box.md)  
 プロセス ビューで特定のプロセスのノードを検索するために使用します。  
  
 [[プロセス プロパティ] ダイアログ ボックス](../debugger/process-properties-dialog-box.md)  
 プロセス ビューで選択したプロセスのプロパティを表示します。  
  
 [Spy++ リファレンス](../debugger/spy-increment-reference.md)  
 各 spy++ メニューおよびダイアログ ボックスについて説明するセクションが含まれています。



