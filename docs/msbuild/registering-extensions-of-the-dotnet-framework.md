---
title: ".NET Framework の拡張機能の登録 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Add References dialog box, registering extensions of the .NET Framework
- MSBuild, registering extensions of the .NET Framework
- .NET Framework extensions, registering
ms.assetid: deee6f53-ea87-4b88-a120-bea589822e03
caps.latest.revision: "5"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 5e9ab37b054dd137590b38dcd62d2de7ebdd1cd1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="registering-extensions-of-the-net-framework"></a>.NET Framework の拡張機能の登録
.NET Framework の特定のバージョンを拡張するアセンブリを開発できます。 アセンブリが Visual Studio の **[参照の追加]** ダイアログ ボックスに表示されるようにするには、そのアセンブリを格納するフォルダーをシステム レジストリに追加する必要があります。  
  
 たとえば、Trey Research 社では、.NET Framework 4 を拡張するライブラリを開発しており、プロジェクトが .NET Framework 4 を対象とするときはそのライブラリ アセンブリが **[参照の追加]** ダイアログ ボックスに表示されるようにするとします。 また、アセンブリは、32 ビット コンピューター上で実行される 32 ビット アセンブリまたは 64 ビット コンピューター上で実行される 64 ビット アセンブリであり、C:\TreyResearch\Extensions4\ フォルダーにインストールされるとします。  
  
 このフォルダーを登録するために使用するキーは、HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\ です。 このキーに指定する既定値は、C:\TreyResearch\Extensions4 です。  
  
> [!NOTE]
>  .NET Framework のビルド番号は異なる場合があります。  
  
 32 ビット アセンブリを 64 ビット コンピューターに登録するには、Wow6432 ノードを使用します (例: HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\)。  
  
## <a name="see-also"></a>参照  
 [Visual Studio の統合](../msbuild/visual-studio-integration-msbuild.md)