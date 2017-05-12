---
title: "Visio オブジェクト モデルの概要"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visio [Visual Studio での Office 開発]、オブジェクト モデル"
  - "オブジェクト モデル [Visual Studio での Office 開発]、Office"
  - "オブジェクト モデル [Visual Studio での Office 開発]、Visio"
  - "オブジェクト [Visual Studio での Office 開発]、Office オブジェクト モデル"
  - "Office オブジェクト モデル"
  - "Visio オブジェクト モデル"
ms.assetid: 11f0ae0c-feff-46c7-9885-b968391718f7
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Visio オブジェクト モデルの概要
  Visio オブジェクト モデルと対話することにより、Microsoft Office Visio 用の Office ソリューションを開発できます。 このオブジェクト モデルは、Visio のプライマリ相互運用機能アセンブリで提供されるクラスとインターフェイスで構成されています。それらは Microsoft.Office.Interop.Visio 名前空間の中で定義されています。  
  
 ここでは、Visio オブジェクト モデルの概要を簡単に説明します。 Office プロジェクトでタスクを実行するために Visio オブジェクト モデルを使用する方法については、次のトピックを参照してください。  
  
-   [Visio 図面の操作](../vsto/working-with-visio-documents.md)  
  
-   [Visio の図形の操作](../vsto/working-with-visio-shapes.md)  
  
## Visio オブジェクト モデルについて  
 Visio では、多くのオブジェクトが操作対象になります。 これらのオブジェクトは、ユーザー インターフェイスとほぼ同様の階層形式で編成されています。 階層の最上位にあるのは、[Microsoft.Office.Interop.Visio.Application](HV10077088) オブジェクトです。 このオブジェクトは、Visio の現在のインスタンスを表します。Microsoft.Office.Interop.Visio.Application オブジェクトには、Microsoft.Office.Interop.Visio.Document オブジェクトと Microsoft.Office.Interop.Visio.Page  オブジェクト、および Microsoft.Office.Interop.Visio.Documents コレクションと Microsoft.Office.Interop.Visio.Pages コレクションが含まれています。 これらのオブジェクトとコレクションにはそれぞれ数多くのメソッドとプロパティがあり、それらにアクセスしてオブジェクトを処理したり、オブジェクトと対話したりできます。  
  
 詳細については、[Microsoft.Office.Interop.Visio.Application](HV10077088)、[Microsoft.Office.Interop.Visio.Document](HV10077095)、および [Microsoft.Office.Interop.Visio.Page](HV10077063) の各オブジェクト、[Microsoft.Office.Interop.Visio.Documents](HV10077062) および [Microsoft.Office.Interop.Visio.Pages](HV10077074) の各コレクションの VBA リファレンス ドキュメントを参照してください。  
  
 この後のセクションでは、最上位レベルのオブジェクトとそれらの相互関係について、簡単に説明します。 このようなオブジェクトには次の 4 つがあります。  
  
-   Application オブジェクト  
  
-   Document オブジェクト  
  
-   Page オブジェクト  
  
### アプリケーション オブジェクト  
 Microsoft.Office.Interop.Visio.Application オブジェクトは Visio アプリケーションを表し、他のすべてのオブジェクトの親です。 そのメンバーは、通常、Visio 全体に適用されます。Microsoft.Office.Interop.Visio.Application オブジェクトと Microsoft.Office.Interop.Visio.ApplicationSettings オブジェクトのプロパティおよびメソッドを使用して、Visio の環境を制御できます。  
  
 VSTO アドイン プロジェクトで Microsoft.Office.Interop.Visio.Application オブジェクトにアクセスするには、`ThisAddIn` クラスの `Application` フィールドを使用します。 詳細については、「[VSTO アドインのプログラミング](../vsto/programming-vsto-add-ins.md)」を参照してください。  
  
### Document オブジェクト  
 Microsoft.Office.Interop.Visio.Document オブジェクトは、Visio プログラミングの中心となるオブジェクトです。 これは、図面、ステンシル、またはテンプレート ファイルを表します。 Visio 図面を開いたり、新しい図面を作成したりすると、新しい Microsoft.Office.Interop.Visio.Document オブジェクトが作成され、Microsoft.Office.Interop.Visio.Application オブジェクトの Microsoft.Office.Interop.Visio.Documents コレクションに追加されます。  
  
 フォーカスがある文書は、作業中の文書と呼ばれます。 これは Microsoft.Office.Interop.Visio.Application オブジェクトの Microsoft.Office.Interop.Visio.Application.ActiveDocument プロパティによって表されます。  
  
### Page オブジェクト  
 Microsoft.Office.Interop.Visio.Page オブジェクトは、前景ページまたは背景ページの描画領域を表します。Microsoft.Office.Interop.Visio.Page.Background プロパティを使用すると、ページが前景ページと背景ページのどちらであるかを判定できます。  
  
 図形を作成するには、Microsoft.Office.Interop.Visio.Page.DrawSpline メソッドや Microsoft.Office.Interop.Visio.Page.DrawOval メソッドなどのメソッドを使用できます。 さらに、ステンシルからマスターを取得し、Microsoft.Office.Interop.Visio.Page.Drop メソッドまたは Microsoft.Office.Interop.Visio.Page.DropMany メソッドを使用することにより図形をページに配置できます。  
  
## Visio オブジェクト モデル ドキュメントの使用  
 Visio オブジェクト モデルの詳細については、Visio の VBA オブジェクト モデルのリファレンスを参照してください。 VBA オブジェクト モデルのリファレンス ドキュメントでは、Visual Basic for Applications \(VBA\) コードに公開される Visio オブジェクト モデルについて説明しています。 詳細については、「[Visio 2010 Object Model Reference \(Visio 2010 オブジェクト モデル リファレンス\)](http://go.microsoft.com/fwlink/?LinkId=199775)」を参照してください。  
  
 VBA オブジェクト モデルのリファレンス内のオブジェクトとメンバーはすべて、Visio プライマリ相互運用機能アセンブリ \(PIA\) の型とメンバーに対応します。 たとえば、VBA オブジェクト モデルのリファレンスにある Document オブジェクトは、Visio PIA の Microsoft.Office.Interop.Visio.Document 型に対応します。 VBA オブジェクト モデルのリファレンスでは、ほとんどのプロパティ、メソッド、およびイベントのコード例を紹介しています。ただし、Visual Studio を使用して作成した Visio VSTO アドイン プロジェクトでこのリファレンス内の VBA コードを使用するには、それらを Visual Basic または Visual C\# に変換する必要があります。  
  
> [!NOTE]  
>  現在のところ、Visio プライマリ相互運用機能アセンブリに関するリファレンス ドキュメントは提供されていません。  
  
 Visio ソリューションの作成に関連するコード例と追加のツールについては「[Visio 2010 Software Development Kit \(Visio 2010 ソフトウェア開発キット\)](http://go.microsoft.com/fwlink/?LinkId=196501)」を参照してください。  
  
### プライマリ相互運用機能アセンブリの追加の型  
 実装の違いにより VBA には表示されないプライマリ相互運用機能アセンブリの型があります。 VBA では、直接使用できるオブジェクトとメンバーだけを含む Visio オブジェクト モデルのビューが提供されます。 プライマリ相互運用機能アセンブリは同じオブジェクト モデルを公開しますが、それには、COM オブジェクト モデルのオブジェクトをマネージ コードに変換する、その他のインターフェイス、クラス、およびメンバーも含まれています。 これらの追加の項目は、コードで直接使用するためのものではありません。  
  
 詳細については、「[Overview of Classes and Interfaces in the Office Primary Interop Assemblies \(Office プライマリ相互運用機能アセンブリのクラスとインターフェイスの概要\)](http://go.microsoft.com/fwlink/?LinkId=189592)」および「[Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)」を参照してください。  
  
## 参照  
 [Visio ソリューション](../vsto/visio-solutions.md)   
 [Visio 図面の操作](../vsto/working-with-visio-documents.md)   
 [Visio の図形の操作](../vsto/working-with-visio-shapes.md)  
  
  