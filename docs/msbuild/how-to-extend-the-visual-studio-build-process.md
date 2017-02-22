---
title: "方法 : Visual Studio ビルド処理を拡張する | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, DependsOn プロパティ"
  - "MSBuild, 拡張 (Visual Studio ビルドを)"
  - "MSBuild, オーバーライド (DependsOn プロパティを)"
  - "MSBuild, オーバーライド (定義済みターゲットを)"
ms.assetid: cb077613-4a59-41b7-96ec-d8516689163c
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 方法 : Visual Studio ビルド処理を拡張する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ビルド処理は、プロジェクト ファイルにインポートされる一連の [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] .targets ファイルで定義されます。  このインポートされたファイルの 1 つである Microsoft.Common.targets を拡張すると、ビルド処理の複数の箇所でカスタム タスクを実行できます。  ここでは、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ビルド処理の拡張に使用できる 2 つのメソッドについて説明します。  
  
-   Microsoft.Common.targets で定義されている特定の定義済みターゲットのオーバーライド  
  
-   Microsoft.Common.targets で定義されている "DependsOn" プロパティのオーバーライド  
  
## 定義済みターゲットのオーバーライド  
 Microsoft.Common.targets ファイルには、ビルド処理の一部の主要ターゲットの前後に呼び出される、一連の空の定義済みターゲットが含まれています。  たとえば、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] は `CoreBuild` メイン ターゲットの前に `BeforeBuild` ターゲットを呼び出し、`CoreBuild` ターゲットの後に `AfterBuild` ターゲットを呼び出します。  既定では、Microsoft.Common.targets 内の空のターゲットは何も実行しませんが、Microsoft.Common.targets をインポートするプロジェクト ファイルで必要なターゲットを定義することで、既定の動作をオーバーライドできます。  これにより、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] タスクを使用してビルド処理を詳細に制御できます。  
  
#### 定義済みターゲットをオーバーライドするには  
  
1.  オーバーライドする Microsoft.Common.targets 内の定義済みターゲットを識別します。  安全にオーバーライドできるターゲットの完全な一覧については、次の表を参照してください。  
  
2.  プロジェクト ファイルの末尾で、`</Project>` タグの直前にターゲットを定義します。  次に例を示します。  
  
    ```  
    <Project>  
        ...  
        <Target Name="BeforeBuild">  
            <!-- Insert tasks to run before build here -->  
        </Target>  
        <Target Name="AfterBuild">  
            <!-- Insert tasks to run after build here -->  
        </Target>  
    </Project>  
    ```  
  
3.  プロジェクト ファイルをビルドします。  
  
 次の表は、安全にオーバーライドできる Microsoft.Common.targets のすべてのターゲットを示しています。  
  
|ターゲット名|Description|  
|------------|-----------------|  
|`BeforeCompile`, `AfterCompile`|この 2 つのターゲットのいずれかに挿入されたタスクは、コア コンパイルの前または後に実行されます。  ほとんどのカスタマイズは、この 2 つのターゲットのいずれかで行われます。|  
|`BeforeBuild`, `AfterBuild`|この 2 つのターゲットのいずれかに挿入されたタスクは、ビルド内の他のすべての処理の前または後に実行されます。 **Note:**  `BeforeBuild` ターゲットと `AfterBuild` ターゲットは、ほとんどのプロジェクト ファイルの末尾のコメントで既に定義されています。  これにより、ビルド前イベントとビルド後イベントをプロジェクト ファイルに簡単に追加できます。|  
|`BeforeRebuild`, `AfterRebuild`|この 2 つのターゲットのいずれかに挿入されたタスクは、コア リビルド機能が呼び出される前または後に実行されます。  Microsoft.Common.targets でターゲットは、`BeforeRebuild`、`Clean`、`Build`、`AfterRebuild` の順序で実行されます。|  
|`BeforeClean`, `AfterClean`|この 2 つのターゲットのいずれかに挿入されたタスクは、コア クリーン機能が呼び出される前または後に実行されます。|  
|`BeforePublish`, `AfterPublish`|この 2 つのターゲットのいずれかに挿入されたタスクは、コア発行機能が呼び出される前または後に実行されます。|  
|`BeforeResolveReference`, `AfterResolveReferences`|この 2 つのターゲットのいずれかに挿入されたタスクは、アセンブリ参照が解決される前または後に実行されます。|  
|`BeforeResGen`, `AfterResGen`|この 2 つのターゲットのいずれかに挿入されたタスクは、リソースが生成される前または後に実行されます。|  
  
## "DependsOn" プロパティのオーバーライド  
 定義済みのターゲットをオーバーライドすると、ビルド処理を簡単に拡張できますが、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] はターゲットの定義を順番に評価するため、プロジェクトをインポートする別のプロジェクトが、既にオーバーライドしたターゲットをオーバーライドすることは避けられません。  したがって、たとえば、プロジェクト ファイルで定義されている最後の `AfterBuild` ターゲットは、他のすべてのプロジェクトがインポートされた後、ビルド中に使用されるターゲットになります。  
  
 Microsoft.Common.targets ファイルの `DependsOnTargets` 属性で使用される "DependsOn" プロパティをオーバーライドすることで、意図しないターゲットのオーバーライドを防ぐことができます。  たとえば、`Build` ターゲットには、`"$(BuildDependsOn)"` の `DependsOnTargets` 属性値が含まれています。  次の例を考えてみましょう。  
  
```  
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>  
```  
  
 この XML は、`Build` ターゲットを実行する前に、`BuildDependsOn` プロパティで指定されているすべてのターゲットを実行する必要があることを示しています。  `BuildDependsOn` プロパティは、次のように定義されています。  
  
```  
<PropertyGroup>  
    <BuildDependsOn>  
        BeforeBuild;  
        CoreBuild;  
        AfterBuild  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 プロジェクト ファイルの末尾で `BuildDependsOn` という名前の別のプロパティを宣言することで、このプロパティ値をオーバーライドできます。  新しいプロパティに前の `BuildDependsOn` プロパティを含めることで、ターゲット一覧の先頭と末尾に新しいターゲットを追加できます。  次に例を示します。  
  
```  
<PropertyGroup>  
    <BuildDependsOn>  
        MyCustomTarget1;  
        $(BuildDependsOn);  
        MyCustomTarget2  
    </BuildDependsOn>  
</PropertyGroup>  
  
<Target Name="MyCustomTarget1">  
    <Message Text="Running MyCustomTarget1..."/>  
</Target>  
<Target Name="MyCustomTarget2">  
    <Message Text="Running MyCustomTarget2..."/>  
</Target>  
```  
  
 プロジェクト ファイルをインポートするプロジェクトは、ユーザーが実行したカスタマイズを上書きしなくても、これらのプロパティをオーバーライドできます。  
  
#### "DependsOn" プロパティをオーバーライドするには  
  
1.  オーバーライドする Microsoft.Common.targets 内の定義済みの "DependsOn" プロパティを識別します。  一般的にオーバーライドされる "DependsOn" プロパティの一覧については、次の表を参照してください。  
  
2.  プロジェクト ファイルの末尾で、プロパティの別のインスタンスを定義します。  `$(BuildDependsOn)` などの元のプロパティを新しいプロパティに含めます。  
  
3.  プロパティ定義の前または後にカスタム ターゲットを定義します。  
  
4.  プロジェクト ファイルをビルドします。  
  
### 一般的にオーバーライドされる "DependsOn" プロパティ  
  
|プロパティ名|Description|  
|------------|-----------------|  
|`BuildDependsOn`|ビルド処理全体の前または後にカスタム ターゲットを挿入する場合にオーバーライドするプロパティ。|  
|`CleanDependsOn`|カスタム ビルド処理から出力をクリーンアップする場合にオーバーライドするプロパティ。|  
|`CompileDependsOn`|コンパイル処理の前または後にカスタム プロセスを挿入する場合にオーバーライドするプロパティ。|  
  
## 参照  
 [Visual Studio の統合](../msbuild/visual-studio-integration-msbuild.md)   
 [MSBuild の概念](../msbuild/msbuild-concepts.md)   
 [.Targets Files](../msbuild/msbuild-dot-targets-files.md)