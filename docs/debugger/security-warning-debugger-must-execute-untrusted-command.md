---
title: 'セキュリティの警告: デバッガーは信頼されないコマンドを実行する必要があります |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.securityalert
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 77554795772a5a9e2ce5d9bbe9f620923bc20184
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31479930"
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>セキュリティ警告 : デバッガーは信頼されないコマンドを実行する必要があります
ソース サーバーを使用している場合、この警告ダイアログ ボックスが表示されます。 デバッガーがソース コードを取得するために実行する必要のあるコマンドが、srcsvr.ini ファイルに含まれる、ソース サーバーに対して信頼できるコマンドの一覧に記載されていないことを示します。 このコマンドが有効な場合、srcsvr.ini ファイルに追加できます。 それ以外の場合は、そのコマンドを実行しないようにしてください。 詳細については、[シンボル (.pdb) ファイルとソース ファイルの指定](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)に関する記事をご覧ください。  
  
## <a name="message-text"></a>メッセージ テキスト  
 **デバッガーは、移行元サーバーからソース コードを取得する次の信頼されていないコマンドを実行する必要があります。**  
  
 **場合は、デバッグ シンボル ファイル (\*.pdb) が、既知で信頼できるソースからではなくコマンドは無効なまたは実行に危険である可能性があります。**  
  
 **このコマンドを実行しますか。**  
  
## <a name="uielement-list"></a>UIElement の一覧  
 [テキスト ボックス]  
 実行する .pdb ファイルからのコマンド。  
  
 Run  
 コマンドの実行を許可します。  
  
 [実行しない]  
 コマンドの実行およびソース サーバーからのファイルのダウンロードを停止します。  
  
## <a name="see-also"></a>関連項目  
 [シンボル (.pdb) を指定して、ソース ファイル](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [移行元サーバー](http://msdn.microsoft.com/library/windows/desktop/ms680641\(v=vs.85\).aspx)