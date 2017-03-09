---
title: "Visual Studio の JavaScript | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f3eee13e-30e4-4bc1-81f5-058d7e379b75
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visual Studio の JavaScript
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

JavaScript は Visual Studio の第一級の言語です。  Visual Studio IDE で JavaScript コードを記述する場合に、ほとんどの標準的な編集補助機能 \(コード スニペット、IntelliSense など\) を使用できます。  多くの種類のアプリケーションやサービスの JavaScript コードを記述できます。  
  
 JavaScript の言語リファレンスのドキュメントについては、[JavaScript](http://msdn.microsoft.com/library/d1et7k7c\(v=vs.94\).aspx) を参照してください。  
  
 特定のバージョンの Visual Studio、または特定の Visual Studio 拡張機能では、HTML および JavaScript を使用して特定の種類のアプリケーションとサービスを開発する必要があります。  次の一覧には詳細情報へのリンクがあります。  
  
-   Apache Cordova を使用してクロスプラットフォーム アプリを作成するには、[Apache Cordova 用の Visual Studio Tools を取得](http://go.microsoft.com/fwlink/p/?LinkId=397606) します。  
  
-   [Windows ストア](http://dev.windows.com/develop)、[Windows Phone](http://dev.windows.com/develop)、ユニバーサル アプリ \(両方のプラットフォームをサポートする\) を作成するには、[ツールを取得します](http://dev.windows.com/en-us/develop/downloads)。  
  
-   クラウド ベースのサービスを作成するには、 [「Microsoft Azure サイト」](http://azure.microsoft.com/documentation/)を参照してください。  
  
-   Web サイトと Web アプリを作成するには、[ASP.NET サイトを参照](http://www.asp.net/get-started/websites)してください。  
  
    > [!NOTE]
    >  空の ASP.Net Web サイトを作成して、HTML、CSS、および JavaScript のプログラミング用に使用できます。  ASP.NET によって提供される Webconfig ファイルは、Visual Studio でのデバッグを使用可能にします \(またはアプリの実行時に F12 ツールを使用できます\)。  
  
 Visual Studio の JavaScript エディターでは IntelliSense をサポートしています。  詳細については、「[JavaScript IntelliSense](../ide/javascript-intellisense.md)」を参照してください。  
  
## JavaScript の新機能  
 JavaScript の新機能は、以下の表にリストされています。  
  
|特性|説明|  
|--------|--------|  
|クラス|[クラス](../Topic/class%20Statement%20\(JavaScript\).md)の宣言をサポートする新しい構文です。|  
|Promise|[Promise](../Topic/Promise%20Object%20\(JavaScript\).md) を使用すると、より簡単で読みやすい非同期コーディングができます。  Promise コンストラクターは、`all` および `race` の各ユーティリティ メソッドと一緒にサポートされます。|  
|反復子|反復可能なオブジェクト \(配列、配列に似たオブジェクト、および反復子を含む\) を使用して反復処理を行い、それぞれの別個のプロパティの値に対して実行するステートメントを伴うカスタム反復フックを呼び出すことができるようになりました。  詳細については、「[反復子とジェネレーター](../Topic/Iterators%20and%20Generators%20\(JavaScript\).md)」を参照してください。 **Note:**  ジェネレーターはまだサポートされていません。|  
|アロー関数|アロー関数 \(\=\>\) は、レキシカルな `this` によるバインドの機能を持つ `function` キーワードの略式の構文を提供します。|  
|組み込みオブジェクトの新しいメソッド|[Array オブジェクト](../Topic/Array%20Object%20\(JavaScript\).md)、[Math オブジェクト](../Topic/Math%20Object%20\(JavaScript\).md)、[Number オブジェクト](../Topic/Number%20Object%20\(JavaScript\).md)、[Object オブジェクト](../Topic/Object%20Object%20\(JavaScript\).md)、および [String オブジェクト](../Topic/String%20Object%20\(JavaScript\).md) 組み込みオブジェクトに、データの操作や確認に使用できる多くの新しいユーティリティ関数とプロパティが含まれています。|  
|オブジェクト リテラルの機能強化|オブジェクトにおいて、計算プロパティ、簡潔なメソッドの定義、および同じ名前の変数に値が初期化されるプロパティの略式の構文がサポートされるようになりました。  詳細については、「[オブジェクトの作成](../Topic/Creating%20Objects%20\(JavaScript\).md)」を参照してください。|  
|プロキシ|[プロキシ](../Topic/Proxy%20Object%20\(JavaScript\).md)により、オブジェクトのカスタム動作を設定できます。|  
|rest パラメーター|rest パラメーターを使用すると、関数呼び出しの連続する引数を配列に変換できます。  詳細については、「[関数](../Topic/Functions%20\(JavaScript\).md)」を参照してください。|  
|spread 演算子|[spread 演算子](../Topic/Spread%20Operator%20\(...\)%20\(JavaScript\).md) \(`…`\) は、反復可能な式を個々の引数に展開します。  たとえば、`a.b(…array)` は `a.b.apply(a, array)` とほとんど同じです。|  
|シンボル|[Symbol](../Topic/Symbol%20Object%20\(JavaScript\).md) オブジェクトを使用して既存のオブジェクトにプロパティを追加すると、既存のオブジェクトのプロパティと干渉する可能性がなく、意図せずに可視になる可能性もなく、他のコードから整合性のない追加が実行される可能性もありません。|  
|テンプレート文字列|[テンプレート文字列](../Topic/Template%20Strings%20\(JavaScript\).md)では、その文字列リテラルを式として評価し、そのリテラル文字列に連結することができます。|  
|Unicode の機能強化|Unicode のサポートが向上しました。  たとえば、エスケープ シーケンスの新しい形式では、アストラル コード ポイント \(16 進数字 4 桁を超えるコード ポイント\) がサポートされます。  詳細については、「[特殊文字](../Topic/Special%20Characters%20\(JavaScript\).md)」を参照してください。|  
|WeakSet|[WeakSet](../Topic/WeakSet%20Object%20\(JavaScript\).md) は、他の場所から参照されていない場合にガベージ コレクションの対象となるオブジェクトのコレクションです。|