---
title: '方法: 例外の後にシステム コードを調べる |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, exceptions
- exceptions, debugging
ms.assetid: a38ad49b-7cf3-483d-91c4-eb3116eba50c
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6c66e77a2e5cc7596bb8473678b84f962453df41
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533726"
---
# <a name="how-to-examine-system-code-after-an-exception"></a>方法 : 例外の後にシステム コードを調べる
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: システム コードの後を調べる例外](https://docs.microsoft.com/visualstudio/debugger/how-to-examine-system-code-after-an-exception)します。  
  
例外が発生した場合、システム コール内のコードを調べて、例外の原因を判断する必要がある場合があります。 システム コードのシンボルが読み込まれていない場合、または [マイ コードのみ] が有効な場合にこの操作を行う方法を次の手順に示します。  
  
### <a name="to-examine-system-code-following-an-exception"></a>例外の後にシステム コードを調べるには  
  
1.  **呼び出し履歴**ウィンドウで、右クリックし、をクリックして**外部コードの表示**します。  
  
     [マイ コードのみ] が有効でない場合、ショートカット メニューにこのオプションは表示されず、既定でシステム コードが表示されます。  
  
2.  表示される外部コード フレームを右クリックし、**呼び出し履歴**ウィンドウ。  
  
3.  をポイント**シンボルの読み込み元**し**Microsoft シンボル サーバー**します。  
  
    1.  [マイ コードのみ] が有効な場合、ダイアログ ボックスが表示されます。 [マイ コードのみ] が無効になったことが示されます。 これは、システム コールにステップ インするために必要です。  
  
    2.  **パブリック シンボルをダウンロード** ダイアログ ボックスが表示されます。 このダイアログ ボックスは、ダウンロードが終了すると消えます。  
  
4.  これで、システムのコードを調べることができます、**呼び出し履歴**ウィンドウとその他のウィンドウ。 ソース コードを表示する呼び出しスタック フレームをダブルクリックする、または**逆アセンブル**ウィンドウ。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーでの例外の管理](../debugger/managing-exceptions-with-the-debugger.md)





