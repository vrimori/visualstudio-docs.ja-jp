---
title: ".NET Framework の拡張機能の登録 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[参照の追加] ダイアログ ボックス、登録 (.NET Framework の拡張機能を)"
  - "MSBuild、登録 (.NET Framework の拡張機能を)"
  - ".NET Framework 拡張機能、登録"
ms.assetid: deee6f53-ea87-4b88-a120-bea589822e03
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# .NET Framework の拡張機能の登録
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

.NET Framework の特定のバージョンを拡張するアセンブリを開発できます。  アセンブリが Visual Studio の **\[参照の追加\]** ダイアログ ボックスに表示されるようにするには、そのアセンブリを格納するフォルダーをシステム レジストリに追加する必要があります。  
  
 たとえば、Trey Research 社では、.NET Framework 4 を拡張するライブラリを開発しており、プロジェクトが .NET Framework 4 を対象とするときはそのライブラリ アセンブリが **\[参照の追加\]** ダイアログ ボックスに表示されるようにするとします。  また、アセンブリは、32 ビット コンピューター上で実行される 32 ビット アセンブリまたは 64 ビット コンピューター上で実行される 64 ビット アセンブリであり、C:\\TreyResearch\\Extensions4\\ フォルダーにインストールされるとします。  
  
 このフォルダーを登録するために使用するキーは、HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\.NETFramework\\v4.0.21006\\AssemblyFoldersEx\\TreyResearch\\ です。  このキーに指定する既定値は、C:\\TreyResearch\\Extensions4 です。  
  
> [!NOTE]
>  .NET Framework のビルド番号は異なる場合があります。  
  
 32 ビット アセンブリを 64 ビット コンピューターに登録するには、Wow6432 ノードを使用します \(例: HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\.NETFramework\\v4.0.21006\\AssemblyFoldersEx\\TreyResearch\\\)。  
  
## 参照  
 [Visual Studio の統合](../msbuild/visual-studio-integration-msbuild.md)