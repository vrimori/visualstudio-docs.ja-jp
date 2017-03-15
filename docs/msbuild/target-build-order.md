---
title: "ターゲットのビルド順序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "msbuild, ビルド順序"
ms.assetid: f4a26339-9f9a-497a-9aa6-0797183d450d
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# ターゲットのビルド順序
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

あるターゲットへの入力が別のターゲットの出力に依存する場合、ターゲットの順序を指定する必要があります。  ターゲットの実行順序を指定するには、これらの属性を使用して:  
  
-   `InitialTargets`.  `Project` のこの属性は、ターゲットがコマンド ラインまたは `DefaultTargets` の属性に指定されている場合、最初に実行されるターゲットを指定します。  
  
-   `DefaultTargets`.  この `Project` の atttribute は、ターゲットがコマンド ラインで明示的に指定されていない場合、ターゲットが実行するかを指定します。  
  
-   `DependsOnTargets`.  `Target` のこの属性はこのターゲットを実行する前に実行するターゲットを指定します。  
  
-   `BeforeTargets` および `AfterTargets`。  `Target` のこれらの属性は、このターゲットを指定されたターゲット \(MSBuild 4.0\) の前または後に実行するかを指定します。  
  
 ビルド内の後続のターゲットがそのターゲットに依存している場合でも、ターゲットが 1 回のビルド中に 2 回実行されることはありません。  ターゲットは一度実行されると、それ以上ビルドに影響しません。  
  
 ターゲットには、`Condition` 属性を指定することができます。  指定された条件が `false`と評価された場合、ターゲットは実行されず、ビルドには影響しません。  条件の詳細については、「[Conditions](../msbuild/msbuild-conditions.md)」を参照してください。  
  
## 開始ターゲット  
 [プロジェクト](../msbuild/project-element-msbuild.md) の要素の `InitialTargets` の属性は、ターゲットがコマンド ラインまたは `DefaultTargets` の属性に指定されている場合、最初に実行されるターゲットを指定します。  開始ターゲットは、一般的に、エラー チェックに使用されます。  
  
 `InitialTargets` の属性の値は、ターゲットをセミコロンで区切った順序付きリストです。  次の例では `Warm` のターゲットを実行してから `Eject` ターゲットを実行するように指定しています。  
  
```  
<Project InitialTargets="Warm;Eject" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
```  
  
 インポートされたプロジェクトには、独自の `InitialTargets` 属性が含まれている場合があります。  それらのすべての開始ターゲットが集約されて順番に実行されます。  
  
 詳細については、「[方法 : 最初にビルドするターゲットを指定する](../msbuild/how-to-specify-which-target-to-build-first.md)」を参照してください。  
  
## 既定のターゲット  
 [プロジェクト](../msbuild/project-element-msbuild.md) の要素の `DefaultTargets` の属性は、ターゲットがコマンド ラインで明示的に指定しないターゲット組み込まれたを指定します。  
  
 `DefaultTargets` の属性の値は、既定のターゲットをセミコロン区切り、並べた一覧になります。  次の例では `Clean` のターゲットを実行してから `Build` ターゲットを実行するように指定しています。  
  
```  
<Project DefaultTargets="Clean;Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
```  
  
 コマンド ラインの **\/target** スイッチによって既定のターゲットをオーバーライドできます。  次の例では `Build` のターゲットを実行してから `Report` ターゲットを実行するように指定しています。  この方法でターゲットを指定する場合、既定のターゲットは無視されます。  
  
 `msbuild /target:Build;Report`  
  
 開始ターゲットとの両方を既定のターゲットが指定されており、コマンド ラインでターゲットが指定されていない場合、MSBuild は最初のターゲットが実行されてから既定のターゲットが実行されます。  
  
 インポートされたプロジェクトには、独自の `DefaultTargets` 属性が含まれている場合があります。  実行される既定のターゲットは、最初にある `DefaultTargets` 属性によって決まります。  
  
 詳細については、「[方法 : 最初にビルドするターゲットを指定する](../msbuild/how-to-specify-which-target-to-build-first.md)」を参照してください。  
  
## 最初のターゲット  
 開始ターゲット、既定のターゲット、コマンド ラインのターゲットがいずれも指定されていない場合、プロジェクト ファイル内またはインポートされたプロジェクト ファイル内にある最初のターゲットが実行されます。  
  
## ターゲットの依存関係  
 ターゲットには、他のターゲットとの依存関係を記述できます。  `DependsOnTargets` 属性は、ターゲットが他のターゲットに依存していることを示します。  次に例を示します。  
  
```  
<Target Name="Serve" DependsOnTargets="Chop;Cook" />  
```  
  
 `Serve` のターゲットが `Chop` のターゲットと `Cook` のターゲットに依存するように MSBuild に指示します。  MSBuild は `Serve` のターゲットを実行する前に `Chop` のターゲットを実行してから `Cook` のターゲットが実行されます。  
  
## の後のターゲットの前とターゲット  
 MSBuild 4.0 では、`BeforeTargets` 属性と `AfterTargets` 属性を使用してターゲットの順序を指定できます。  
  
 次のようなスクリプトがあるとします。  
  
```  
<Project DefaultTargets="Compile;Link" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Compile">  
        <Message Text="Compiling" />  
    </Target>  
    <Target Name="Link">  
        <Message Text="Linking" />  
    </Target>  
</Project>  
```  
  
 後 `Compile` が、ターゲットの実行前に `Link` のターゲット、`Project` の要素に次のターゲットを任意の場所に追加 `Optimize` 中間ターゲットを作成します。  
  
```  
<Target Name="Optimize"   
    AfterTargets="Compile" BeforeTargets="Link">  
    <Message Text="Optimizing" />  
</Target>  
```  
  
## ターゲットのビルド順序の決定  
 MSBuild では、次のようにしてターゲットのビルド順序を決定します。  
  
1.  `InitialTargets` のターゲットが実行されます。  
  
2.  コマンド ラインで **\/target** スイッチを使用して指定されたターゲットが実行されます。  コマンド ラインでターゲットを指定しない場合は、`DefaultTargets` のターゲットが実行されます。  いずれも指定されていない場合、最初のターゲットが実行されます。  
  
3.  ターゲットの `Condition` 属性が評価されます。  `Condition` の属性があり、`false`と評価されると、ターゲットは実行されず、ビルドにはそれ以上の効果はありません。  
  
4.  ターゲットの実行前に、そのターゲットの `DependsOnTargets` ターゲットが実行されます。  
  
5.  ターゲットの実行前に、そのターゲットを `BeforeTargets` 属性で指定しているターゲットが実行されます。  
  
6.  ターゲットの実行前に、そのターゲットの `Inputs` 属性と `Outputs` 属性が比較されます。  どの出力ファイルが対応する入力ファイルに対して最新ではないと判断された場合、ターゲットは実行されます。  最新である場合は、ターゲットはスキップされます。  
  
7.  ターゲットが実行またはスキップされた後に、そのターゲットを `AfterTargets` 属性で指定しているターゲットが実行されます。  
  
## 参照  
 [ターゲット](../msbuild/msbuild-targets.md)