---
title: 'セキュリティの警告: デバッガーは信頼されていないコマンドを実行する必要があります |Microsoft Docs'
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
- vs.debug.sourceserver.securityalert
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7582004372c5b3de7fdcc23398e4aacf128fcbb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533385"
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>セキュリティ警告 : デバッガーは信頼されないコマンドを実行する必要があります
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[セキュリティ警告: デバッガー Must Execute Untrusted Command](https://docs.microsoft.com/visualstudio/debugger/security-warning-debugger-must-execute-untrusted-command)します。  
  
ソース サーバーを使用している場合、この警告ダイアログ ボックスが表示されます。 デバッガーがソース コードを取得するために実行する必要のあるコマンドが、srcsvr.ini ファイルに含まれる、ソース サーバーに対して信頼できるコマンドの一覧に記載されていないことを示します。 このコマンドが有効な場合、srcsvr.ini ファイルに追加できます。 それ以外の場合は、そのコマンドを実行しないようにしてください。 詳細については、[シンボル (.pdb) ファイルとソース ファイルの指定](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)に関する記事をご覧ください。  
  
## <a name="message-text"></a>メッセージ テキスト  
 **デバッガーでは、移行元サーバーからソース コードを取得する次の信頼されていないコマンドを実行する必要があります。**  
  
 **場合は、デバッグ シンボル ファイル (\*.pdb) がない既知または信頼されたソースでは、このコマンドである可能性が無効であるかを実行するは危険です。**  
  
 **このコマンドを実行しますか。**  
  
## <a name="uielement-list"></a>UIElement の一覧  
 [テキスト ボックス]  
 実行する .pdb ファイルからのコマンド。  
  
 Run  
 コマンドの実行を許可します。  
  
 [実行しない]  
 コマンドの実行およびソース サーバーからのファイルのダウンロードを停止します。  
  
## <a name="see-also"></a>関連項目  
 [シンボル (.pdb) を指定し、ソース ファイル](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [移行元サーバー](http://msdn.microsoft.com/library/windows/desktop/ms680641\(v=vs.85\).aspx)



