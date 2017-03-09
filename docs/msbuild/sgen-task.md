---
title: "SGen Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#SGen"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "SGen task [MSBuild]"
  - "MSBuild, SGen task"
ms.assetid: 22c5ade4-4159-4667-b891-0c1aa06f4df5
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# SGen Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定されたアセンブリの種類に対応する XML シリアル化アセンブリを作成します。  このタスクは、XML シリアライザー ジェネレーター ツール \(Sgen.exe\) をラップするタスクです。  詳細については、「[XML シリアライザー ジェネレーター ツール \(Sgen.exe\)](../Topic/XML%20Serializer%20Generator%20Tool%20\(Sgen.exe\).md)」を参照してください。  
  
## パラメーター  
 `SGen` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|Description|  
|------------|-----------------|  
|`BuildAssemblyName`|必須の `String` 型のパラメーターです。<br /><br /> シリアル化コードを生成するアセンブリです。|  
|`BuildAssemblyPath`|必須の `String` 型のパラメーターです。<br /><br /> シリアル化コードを生成するアセンブリのパスです。|  
|`DelaySign`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> 完全署名されたアセンブリを作成する場合は、`true` を設定します。  アセンブリに公開キーだけを含める場合は、`false` を設定します。<br /><br /> `KeyFile` パラメーターまたは `KeyContainer` パラメーターと一緒に使用しない場合、このパラメーターは無効になります。|  
|`KeyContainer`|省略可能な `String` 型のパラメーターです。<br /><br /> キー ペアを保持するコンテナーを指定します。  こうすると、アセンブリ マニフェストに公開キーを挿入することによって、アセンブリに対する署名が行われます。  次に、タスクは最終的なアセンブリに秘密キーで署名します。|  
|`KeyFile`|省略可能な `String` 型のパラメーターです。<br /><br /> アセンブリに署名するためのキー ペアまたは公開キーを指定します。  コンパイラは、アセンブリ マニフェストに公開キーを挿入し、最終的なアセンブリに秘密キーで署名します。|  
|`Platform`|省略可能な `String` 型のパラメーターです。<br /><br /> 出力アセンブリの生成に使用されるコンパイラ プラットフォームを取得または設定します。  このパラメーターの値には、`x86`、`x64`、または `anycpu` を指定できます。  既定値は `anycpu` です。|  
|`References`|省略可能な `String[]` 型のパラメーターです。<br /><br /> XML シリアル化で必要な型によって参照されるアセンブリを指定します。|  
|`SdkToolsPath`|省略可能な `String` 型のパラメーターです。<br /><br /> resgen.exe などの SDK ツールのパスを指定します。|  
|`SerializationAssembly`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の出力パラメーター。<br /><br /> 生成されたシリアル化アセンブリが格納されます。|  
|`SerializationAssemblyName`|省略可能な `String` 型のパラメーターです。<br /><br /> 生成されるシリアル化アセンブリの名前を指定します。|  
|`ShouldGenerateSerializer`|必須の `Boolean` 型のパラメーターです。<br /><br /> `true` の場合、SGen タスクでシリアル化アセンブリを生成する必要があります。|  
|`Timeout`|省略可能な `Int32` 型のパラメーターです。<br /><br /> タスク実行を終了するまでの時間をミリ秒単位で指定します。  既定値は `Int.MaxValue` であり、タイムアウト期限がないことを示します。|  
|`ToolPath`|省略可能な `String` 型のパラメーターです。<br /><br /> タスクで基になる実行可能ファイル \(sgen.exe\) を読み込む場所を指定します。  このパラメーターを指定しないと、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] を実行しているフレームワークのバージョンに対応する SDK インストール パスが使用されます。|  
|`Types`|省略可能な `String[]` 型のパラメーターです。<br /><br /> シリアル化コードを生成する特定の型の一覧を取得または設定します。  SGen は、これらの型に対してのみ、シリアル化コードを生成します。|  
|`UseProxyTypes`|必須の `Boolean` 型のパラメーターです。<br /><br /> `true` の場合、SGen タスクでは XML Web サービス プロキシ型に対してのみシリアル化コードを生成します。|  
  
## 解説  
 上記のパラメーター以外に、このタスクは <xref:Microsoft.Build.Tasks.ToolTaskExtension> クラスからパラメーターを継承します。このクラス自体は、<xref:Microsoft.Build.Utilities.ToolTask> クラスから継承されます。  これらの追加のパラメーターの一覧とその説明については、「[ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md)」を参照してください。  
  
## 参照  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [タスク](../msbuild/msbuild-tasks.md)   
 [MSBuild の概念](../msbuild/msbuild-concepts.md)