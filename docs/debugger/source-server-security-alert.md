---
title: ソース サーバーのセキュリティ警告 |Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f732586581c1e7c4634d4a3d7e9d904cd5ea46ca
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54991477"
---
# <a name="source-server-security-alert"></a>ソース サーバー のセキュリティ警告
ソース サーバーの使用時は、認識できて信頼できる場所からのシンボル ファイルのみを使用してください。  
  
 ソース サーバーのサポートを有効にすると、この警告が表示されます。 ソース サーバーのコマンドは、デバッグ シンボル ファイル (**\*.pdb** ファイル) に埋め込まれています。 PDB ファイルの作成元を確認してください。  
  
> [!IMPORTANT]
>  次の潜在的なセキュリティの脅威は、移行元サーバーを使用する場合を考慮する必要があります。アプリケーションの .pdb ファイルには任意のコマンドを埋め込むことができるため、srcsrv.ini ファイルには実行するコマンドのみ配置するようにします。 srcsvr.ini ファイルにないコマンドを実行しようとすると、確認のダイアログ ボックスが表示されます。 詳細については、次を参照してください。[セキュリティ警告。デバッガーは信頼されないコマンドを実行する必要があります](../debugger/security-warning-debugger-must-execute-untrusted-command.md)。 コマンド パラメーターでは何も検証されないため、コマンドを信頼するときは注意してください。 たとえば、cmd.exe を信頼した場合、悪意のあるユーザーが危険な動作を実行するようにコマンドにパラメーターを指定する可能性があります。  
  
## <a name="see-also"></a>「  
 [シンボル (.pdb) とソース ファイルの指定](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [ソース サーバー](/windows/desktop/Debug/source-server-and-source-indexing)
