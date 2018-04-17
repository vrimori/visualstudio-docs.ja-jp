---
title: '方法: 例外の後にシステム コードを調べる |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, exceptions
- exceptions, debugging
ms.assetid: a38ad49b-7cf3-483d-91c4-eb3116eba50c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2914aab911d3c700b38c58eac009b2e21e94420e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-examine-system-code-after-an-exception"></a>方法 : 例外の後にシステム コードを調べる
例外が発生した場合、システム コール内のコードを調べて、例外の原因を判断する必要がある場合があります。 システム コードのシンボルが読み込まれていない場合、または [マイ コードのみ] が有効な場合にこの操作を行う方法を次の手順に示します。  
  
### <a name="to-examine-system-code-following-an-exception"></a>例外の後にシステム コードを調べるには  
  
1.  **呼び出し履歴**ウィンドウで、右クリックし、をクリックして**外部コードの表示**です。  
  
     [マイ コードのみ] が有効でない場合、ショートカット メニューにこのオプションは表示されず、既定でシステム コードが表示されます。  
  
2.  今すぐに表示される外部コード フレームを右クリックし、**呼び出し履歴**ウィンドウです。  
  
3.  指す**シンボルの読み込み元** をクリックし、 **Microsoft シンボル サーバー**です。  
  
    1.  [マイ コードのみ] が有効な場合、ダイアログ ボックスが表示されます。 [マイ コードのみ] が無効になったことが示されます。 これは、システム コールにステップ インするために必要です。  
  
    2.  **パブリック シンボルをダウンロードする** ダイアログ ボックスが表示されます。 このダイアログ ボックスは、ダウンロードが終了すると消えます。  
  
4.  システム コードを調べてこれで、**呼び出し履歴**ウィンドウおよび他のウィンドウ。 たとえば、ソース コードを表示するコール スタック フレームをダブルクリックしてまたは**逆アセンブル**ウィンドウです。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーでの例外の管理](../debugger/managing-exceptions-with-the-debugger.md)