---
title: ソース サーバーのセキュリティ警告 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.enablewarning
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 8451c281-6914-469c-b80c-6271cc3f3d17
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dbb2233ffcc041a9d756ff51ac9fd3f1b9dc669e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="source-server-security-alert"></a>ソース サーバー のセキュリティ警告
ソース サーバーの使用時は、認識できて信頼できる場所からのシンボル ファイルのみを使用してください。  
  
 ソース サーバーのサポートを有効にすると、この警告が表示されます。 ソース サーバーのコマンドは、デバッグ シンボル ファイルに埋め込まれている (***.pdb**ファイル)。 PDB ファイルの作成元を確認してください。  
  
> [!IMPORTANT]
>  ソース サーバーを使用する場合、注意が必要なセキュリティ上の脅威があります。たとえば、アプリケーションの PDB ファイルには任意のコマンドを埋め込むことができます。そのため、srcsrv.ini ファイルには、実行するコマンドのみを配置するようにします。 srcsvr.ini ファイルにないコマンドを実行しようとすると、確認のダイアログ ボックスが表示されます。 詳細については、「 [Security Warning: Debugger Must Execute Untrusted Command](../debugger/security-warning-debugger-must-execute-untrusted-command.md)」を参照してください。 コマンド パラメーターでは何も検証されないため、コマンドを信頼するときは注意してください。 たとえば、cmd.exe を信頼した場合、悪意のあるユーザーが危険な動作を実行するようにコマンドにパラメーターを指定する可能性があります。  
  
## <a name="see-also"></a>関連項目  
 [シンボル (.pdb) を指定して、ソース ファイル](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [移行元サーバー](http://msdn.microsoft.com/library/windows/desktop/ms680641.aspx)
