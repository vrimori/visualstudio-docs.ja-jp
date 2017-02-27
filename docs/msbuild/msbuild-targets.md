---
title: "MSBuild ターゲット | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, ターゲット"
ms.assetid: 8060b4d2-e4a9-48cf-a437-852649ceb417
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# MSBuild ターゲット
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ターゲットはタスクを特定の順序でグループ化し、ビルド処理を小さな単位に分割できるようにします。  たとえば、1 つのターゲットで出力ディレクトリ内のすべてのファイルを削除してビルドの準備を行い、別のターゲットでプロジェクトの入力をコンパイルして空のディレクトリに配置できます。  タスクの詳細については、「[タスク](../msbuild/msbuild-tasks.md)」を参照してください。  
  
## プロジェクト ファイルでのターゲットの宣言  
 ターゲットは、プロジェクト ファイル内で、[Target](../msbuild/target-element-msbuild.md) 要素を使用して宣言します。  たとえば、次の XML では、Compile 項目の種類をパラメーターに指定して、Csc タスクを呼び出す、Construct という名前のターゲットを作成しています。  
  
```  
<Target Name="Construct">  
    <Csc Sources="@(Compile)" />  
</Target>  
```  
  
 MSBuild プロパティと同様、ターゲットは再定義できます。  次に例を示します。  
  
```  
<Target Name="AfterBuild" >  
    <Message Text="First occurrence" />  
</Target>  
<Target Name="AfterBuild" >  
    <Message Text="Second occurrence" />  
</Target>  
```  
  
 AfterBuild が実行されると、"Second occurrence" とだけ表示されます。  
  
## ターゲットのビルド順序  
 あるターゲットへの入力が別のターゲットの出力に依存する場合、ターゲットの順序を指定する必要があります。  ターゲットの実行順序を指定するには、いくつかの方法があります。  
  
-   開始ターゲット  
  
-   既定のターゲット  
  
-   最初のターゲット  
  
-   ターゲットの依存関係  
  
-   `BeforeTargets` および `AfterTargets` \(MSBuild 4.0\)  
  
 ビルド内の後続のターゲットがそのターゲットに依存している場合でも、ターゲットが 1 回のビルド中に 2 回実行されることはありません。  ターゲットは一度実行されると、それ以上ビルドに影響しません。  
  
 ターゲットのビルド順序の詳細については、「[ターゲットのビルド順序](../msbuild/target-build-order.md)」を参照してください。  
  
## ターゲットのバッチ  
 ターゲット要素には、%\(Metadata\) という形式でメタデータを指定する `Outputs` 属性を指定できます。  その場合、一意のメタデータ値ごとにターゲットが 1 回実行されます。そのメタデータ値を持つ項目は、グループ化または "バッチ処理" されます。  次に例を示します。  
  
```  
<ItemGroup>  
    <Reference Include="System.Core">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="System.Xml.Linq">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="Microsoft.CSharp">  
      <RequiredTargetFramework>4.0</RequiredTargetFramework>  
    </Reference>  
</ItemGroup>  
<Target Name="AfterBuild"  
    Outputs="%(Reference.RequiredTargetFramework)">  
    <Message Text="Reference:  
      @(Reference->'%(RequiredTargetFramework)')" />  
</Target>  
```  
  
 RequiredTargetFramework メタデータによって Reference 項目がバッチ処理されます。  ターゲットの出力は次のようになります。  
  
```  
Reference: 3.5;3.5  
Reference: 4.0  
  
```  
  
 実際のビルドでは、ターゲットのバッチはめったに使用されません。  タスクのバッチの方が一般的です。  詳細については、「[バッチ](../msbuild/msbuild-batching.md)」を参照してください。  
  
## インクリメンタル ビルド  
 インクリメンタル ビルドは、対応する入力ファイルに対して最新の状態の出力ファイルを含むターゲットが実行されないように最適化されたビルドです。  ターゲット要素には、ターゲットが入力として受け取る項目と、ターゲットが出力として生成する項目を示す、`Inputs` 属性と `Outputs` 属性の両方を指定できます。  
  
 すべての出力項目が最新の状態である場合、ターゲットはスキップされるので、ビルド速度が大幅に向上します。  これをターゲットのインクリメンタル ビルドと呼びます。  一部のファイルだけが最新の状態である場合、最新の項目を除いてターゲットが実行されます。  これをターゲットの部分インクリメンタル ビルドと呼びます。  詳細については、「[インクリメンタル ビルド](../msbuild/incremental-builds.md)」を参照してください。  
  
## 参照  
 [MSBuild の概念](../msbuild/msbuild-concepts.md)   
 [方法 : 複数のプロジェクト ファイルで同じターゲットを使用する](../Topic/How%20to:%20Use%20the%20Same%20Target%20in%20Multiple%20Project%20Files.md)