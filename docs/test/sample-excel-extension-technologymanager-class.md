---
title: "Excel 拡張子のサンプル: TechnologyManager クラス | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8a7b760d-b5ac-4451-9593-6ac1a0b95cdb
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "mlearned"
manager: "douge"
---
# Excel 拡張子のサンプル: TechnologyManager クラス
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このクラスは <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager> クラスを拡張し、[!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] 拡張機能のコア サービスを提供します。  基本クラスには多くのメソッドがありますが、このサンプルではその一部のみを使用します。  
  
 一部のメソッドは、単にプロパティの値を返します。  多くのメソッドは、コード化された UI テスト エンジンに組み込まれている既定のアルゴリズムを開発者がオーバーライドできるようにするために用意されています。  これらのメソッドは、<xref:System.NotSupportedException> をスローするか、`null` を返して、フレームワークに既定のアルゴリズムを使用するように指示します。  
  
 基になるテクノロジの複雑さに応じて、テクノロジ マネージャーのコードの開発には数週間から数か月かかる場合があります。  Excel を使用すると、非常に広範なテクノロジ マネージャーを作成できる可能性があります。  この例では、意図的に Excel のワークシートとセルだけに限定し、使用する形式も制限しています。  
  
 可能であれば、テクノロジ マネージャー コードは `Communicator` クラスによって開かれた .NET リモート処理チャネルを使用し、Excel プロセスで実行されているアドインから情報を抽出します。  
  
## COM の参照範囲  
 このクラスと、<xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> クラスを拡張した各要素クラスのすべてに <xref:System.Runtime.InteropServices.ComVisibleAttribute> があり、COM からそのクラスを参照できるように、値が `true` になっています。  
  
## TechnologyName プロパティ  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.TechnologyName%2A?displayProperty=fullName> プロパティのこのオーバーライドは、拡張の他のすべてのコンポーネントの基になるテクノロジを識別する、一意で意味のある名前を提供する必要があります。  この拡張では、値は "Excel" です。  
  
## GetControlSupportLevel メソッド  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetControlSupportLevel%2A?displayProperty=fullName> メソッドのこのオーバーライドは、指定されたハンドルによって表されるコントロールに対してテクノロジ マネージャーが提供できるサポート レベルを示す数値を返します。  数値が大きくなるほど、コントロールに対するテクノロジ マネージャーのサポート レベルは高くなります。  この場合、メソッドはコントロールが含まれているウィンドウを確認し、それが Excel ワークシートであれば、最も高い値を返します。それ以外の場合は 0 が返され、コントロールはサポートされません。  
  
## 要素を取得するメソッド  
 テクノロジに固有の要素を取得するために、コード化された UI テスト フレームワークによって使用される、いくつかの重要なメソッドがあります。要素を取得するには、ハンドル、画面上の点、または別のテクノロジの要素を指定します。  これらのメソッドのコードは、自己記述的です。  基本メソッドは、次のとおりです。  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetFocusedElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromPoint%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromWindowHandle%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromNativeElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.ConvertToThisTechnology%2A?displayProperty=fullName>  
  
## ParseQueryId メソッド  
 コード化された UI テストの作成時に、ユーザーはテストの一部またはすべてのコントロールのプロパティ値を指定できます。  これらのプロパティ値は、テスト フレームワークによって、検索プロパティ \(テスト中に特定の UI コントロールを見つけるために使用される、名前と値のペア\) を作成するために使用されます。  すべての検索プロパティが全体で、テクノロジの各要素の <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A?displayProperty=fullName> プロパティの値を表しており、これにすべてのコントロールが含まれます。  コントロールはテストの実行中に数回検索しなければならない場合があるので、このメソッドはテクノロジ マネージャーによる特定のコントロールの検索プロパティの解析を最適化できるようにします。  このメソッドは、フレームワークがそのコントロールを後で検索するときに使用できるクッキーも返します。  メソッドのこの実装は、<xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName> メソッドを使用して、検索プロパティを解析します。  
  
## MatchElement メソッド  
 テクノロジ マネージャーでコントロールの検索を行う場合、<xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.Search%2A?displayProperty=fullName> メソッドは、可能な一致の配列を返すように実装するか、<xref:System.NotSupportedException> をスローしてフレームワークが独自の検索アルゴリズムを使用するように実装することができます。  どちらの場合も、<xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.MatchElement%2A> メソッドを実装する必要があり、その実装でも <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName> メソッドが使用されます。  
  
## 移動メソッド  
 これらのメソッドは、指定された要素の親、子、または兄弟を UI 階層から取得します。  コードは単純で、わかりやすいコメントが付けられています。  
  
## GetExcelElement 内部メソッド  
 この内部メソッドは、ウィンドウ ハンドルと Excel 要素についての情報を受け取り、要求された Excel 要素を返します。  
  
## 参照  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>   
 <xref:System.NotSupportedException>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>   
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A>   
 [コード化された UI テストと操作の記録を拡張して Microsoft Exce をサポート](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)