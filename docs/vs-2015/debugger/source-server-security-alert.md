---
title: ソース サーバーのセキュリティ警告 |Microsoft Docs
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
- vs.debug.sourceserver.enablewarning
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 8451c281-6914-469c-b80c-6271cc3f3d17
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b971a05f9cd8873a1dbac3cafe6865ffce238868
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536966"
---
# <a name="source-server-security-alert"></a>ソース サーバー のセキュリティ警告
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ソース サーバーのセキュリティの警告](https://docs.microsoft.com/visualstudio/debugger/source-server-security-alert)します。  
  
ソース サーバーの使用時は、認識できて信頼できる場所からのシンボル ファイルのみを使用してください。  
  
 ソース サーバーのサポートを有効にすると、この警告が表示されます。 ソース サーバーのコマンドは、デバッグ シンボル ファイル (PDB ファイル) に埋め込まれています。 PDB ファイルの作成元を確認してください。  
  
> [!IMPORTANT]
>  ソース サーバーを使用する場合、注意が必要なセキュリティ上の脅威があります。たとえば、アプリケーションの PDB ファイルには任意のコマンドを埋め込むことができます。そのため、srcsrv.ini ファイルには、実行するコマンドのみを配置するようにします。 srcsvr.ini ファイルにないコマンドを実行しようとすると、確認のダイアログ ボックスが表示されます。 詳細については、次を参照してください。[セキュリティ警告: デバッガー Must Execute Untrusted Command](../debugger/security-warning-debugger-must-execute-untrusted-command.md)します。コマンドのパラメーターの検証は行われません、そのコマンドを信頼するように注意してください。 たとえば、cmd.exe を信頼した場合、悪意のあるユーザーが危険な動作を実行するようにコマンドにパラメーターを指定する可能性があります。  
  
## <a name="see-also"></a>関連項目  
 [シンボル (.pdb) を指定し、ソース ファイル](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [移行元サーバー](http://msdn.microsoft.com/library/windows/desktop/ms680641.aspx)



