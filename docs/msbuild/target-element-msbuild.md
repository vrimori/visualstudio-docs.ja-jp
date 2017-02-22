---
title: "Target 要素 (MSBuild) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#Target"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Target 要素 [MSBuild]"
  - "<Target> 要素 [MSBuild]"
ms.assetid: 350f6fc2-86b3-45f2-a31e-ece0e6bd4dca
caps.latest.revision: 34
caps.handback.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Target 要素 (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] を連続的に実行するための一連のタスクを格納します。  
  
## 構文  
  
```  
<Target Name="Target Name"  
        Inputs="Inputs"  
        Outputs="Outputs"  
        Returns="Returns"  
        KeepDuplicateOutputs="true/false"  
        BeforeTargets="Targets"  
        AfterTargets="Targets"  
        DependsOnTargets="DependentTarget"  
        Condition="'String A' == 'String B'">  
        Label="Label">  
    <Task>... </Task>  
    <PropertyGroup>… </PropertyGroup>  
    <ItemGroup>… </ItemGroup>  
    <OnError... />  
</Target>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|`Name`|必須の属性です。<br /><br /> ターゲットの名前。|  
|`Condition`|省略可能な属性です。<br /><br /> 評価する条件です。  条件が `false` と評価された場合、ターゲットではターゲットの本体は実行されず、`DependsOnTargets` 属性に設定されたいずれのターゲットも実行されません。  条件の詳細については、「[Conditions](../msbuild/msbuild-conditions.md)」を参照してください。|  
|`Inputs`|省略可能な属性です。<br /><br /> このターゲットの入力を形成するファイル。  複数のファイルをセミコロンで区切って指定します。  ファイルのタイムスタンプが `Outputs` ファイルのタイムスタンプと `Target` が最新であるかどうかを判断する比較されます。  詳細については、「[インクリメンタル ビルド](../msbuild/incremental-builds.md)」、「[方法 : インクリメンタル ビルドを実行する](../msbuild/how-to-build-incrementally.md)」、および「[変換](../msbuild/msbuild-transforms.md)」を参照してください。|  
|`Outputs`|省略可能な属性です。<br /><br /> このターゲットに出力を形成するファイル。  複数のファイルをセミコロンで区切って指定します。  ファイルのタイムスタンプが `Inputs` ファイルのタイムスタンプと `Target` が最新であるかどうかを判断する比較されます。  詳細については、「[インクリメンタル ビルド](../msbuild/incremental-builds.md)」、「[方法 : インクリメンタル ビルドを実行する](../msbuild/how-to-build-incrementally.md)」、および「[変換](../msbuild/msbuild-transforms.md)」を参照してください。|  
|`Returns`|省略可能な属性です。<br /><br /> このターゲットを呼び出すタスク \(MSBuild タスクなど\) で使用可能になるアイテムのセットです。  複数のターゲットを指定するときは、セミコロン \(;\) で区切ります。  ファイルのターゲットに `Returns` の属性がない場合、出力の属性はこの場合は、代わりに使用されます。|  
|`KeepDuplicateOutputs`|省略可能な Boolean 型の属性です。<br /><br /> `true`が、ターゲットのリターンの同じアイテムへの複数の参照記録されます。  既定では、この属性は `false` です。|  
|`BeforeTargets`|省略可能な属性です。<br /><br /> ターゲット名のセミコロン区切りのリストです。指定した場合は、このターゲットを実行する前に指定されたターゲットであることを示します。  これにより、プロジェクト作成者はこれらを直接変更せずに、既存のターゲットのセットを拡張することができます。  詳細については、「[ターゲットのビルド順序](../msbuild/target-build-order.md)」を参照してください。|  
|`AfterTargets`|省略可能な属性です。<br /><br /> ターゲット名のセミコロン区切りのリストです。  指定した場合は、このターゲットを指定したターゲット実行する必要があることを示します。  これにより、プロジェクト作成者はこれらを直接変更せずに、既存のターゲットのセットを拡張することができます。  詳細については、「[ターゲットのビルド順序](../msbuild/target-build-order.md)」を参照してください。|  
|`DependsOnTargets`|省略可能な属性です。<br /><br /> このターゲットを実行する前、またはトップレベルの依存関係分析を実行する前に、実行する必要のあるターゲットです。  複数のターゲットを指定するときは、セミコロン \(;\) で区切ります。|  
|`Label`|省略可能な属性です。<br /><br /> システムとユーザーの要素を識別するか、注文できる識別子。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[タスク](../msbuild/task-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] タスクのインスタンスを作成し、実行します。  ターゲットには、タスクを 0 個以上指定できます。|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|一連の `Property` のユーザー定義の要素が含まれます。  .NET Framework 3.5 以降では、`Target` の要素は `PropertyGroup` の要素を含む場合があります。|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|一連の `Item` のユーザー定義の要素が含まれます。  .NET Framework 3.5 以降では、`Target` の要素は `ItemGroup` の要素を含む場合があります。  詳細については、「[項目](../msbuild/msbuild-items.md)」を参照してください。|  
|[OnError](../msbuild/onerror-element-msbuild.md)|`ContinueOnError` の属性が失敗したタスクの ErrorAndStop \(または\) の場合 `false`一つ以上のターゲットを実行します。  ターゲットには、`OnError` 要素を 0 個以上指定できます。  `OnError` 要素が存在する場合、これらの要素は `Target` 要素内の最後の要素である必要があります。<br /><br /> `ContinueOnError` の属性については、[Task Element \(MSBuild\)](../msbuild/task-element-msbuild.md)"を参照してください。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[プロジェクト](../msbuild/project-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] プロジェクト ファイルの必須のルート要素です。|  
  
## 解説  
 実行する最初のターゲットは、実行時に指定します。  各ターゲットは他のターゲットに対する依存関係を持つ場合があります。  たとえば、配置用のターゲットは、コンパイル用のターゲットに依存します。  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] エンジンは、`DependsOnTargets` 属性に表示される順序で、依存関係を左から右に実行します。  詳細については、「[ターゲット](../msbuild/msbuild-targets.md)」を参照してください。  
  
 あるターゲットに複数のターゲットが依存関係を持つ場合でも、ターゲットは 1 回のビルド中に 1 度だけ実行されます。  
  
 `Condition` 属性が `false` と評価されたためにターゲットがスキップされた場合でも、そのターゲットがその後ビルドで呼び出され、`Condition` 属性がその時点で `true` と評価された場合は、そのターゲットを実行できます。  
  
 MSBuild 4 よりも前のバージョンでは、`Target` によって、`Outputs` 属性で指定されていたすべてのアイテムが返されていました。  このために、MSBuild では、後でビルドのタスクによって要求された場合に備えてこれらのアイテムを記録しておく必要がありました。  呼び出し元が必要とする出力を持つターゲットを示す方法がなかったため、呼び出されたすべての `Target` のすべての `Outputs` から全アイテムを蓄積していました。  これにより、大量の出力アイテムがあるビルドでスケーリングの問題が発生していました。  
  
 ユーザーがプロジェクトの `Target` 要素で `Returns` を指定した場合、`Returns` 属性を持つ `Target` だけがそれらのアイテムを記録します。  
  
 `Target` には、`Outputs` 属性と `Returns` 属性の両方を含めることができます。  `Outputs` と `Inputs` を組み合わせて使用して、ターゲットが最新かどうかを確認します。  `Returns` がある場合、`Outputs` の値がオーバーライドされ、どのアイテムが呼び出し元に返されるかが判断されます。  `Returns` がない場合、前述の場合を除いて、呼び出し元が `Outputs` を使用できるようになります。  
  
 MSBuild 4 よりも前のバージョンでは、`Target` の `Outputs` に同じアイテムへの複数の参照が含まれている場合は、常にそれらの重複アイテムが記録されていました。  そのため、大量の出力と多数のプロジェクトの相互依存関係がある非常に大規模なビルドでは、無用な重複アイテムが原因で、大量のメモリが無駄に使用されていました。  `KeepDuplicateOutputs` の属性が `true`に設定した場合、これらの重複するが記録されます。  
  
## 使用例  
 次のコード例は、`Csc` タスクを実行する `Target` 要素を示しています。  
  
```  
<Target Name="Compile" DependsOnTargets="Resources" Returns="$(TargetPath)">  
    <Csc Sources="@(CSFile)"  
          TargetType="library"  
          Resources="@(CompiledResources)"  
          EmitDebugInformation="$(includeDebugInformation)"  
          References="@(Reference)"  
          DebugType="$(debuggingType)" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
    </Csc>  
</Target>  
```  
  
## 参照  
 [ターゲット](../msbuild/msbuild-targets.md)   
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)