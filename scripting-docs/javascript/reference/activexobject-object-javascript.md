---
title: "ActiveXObject オブジェクト (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "ActiveXObject"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ActiveXObject オブジェクト"
  - "オートメーション オブジェクト, ActiveXObject オブジェクト"
ms.assetid: 9c7bed07-853f-48aa-92db-3131324746ec
caps.latest.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 34
---
# ActiveXObject オブジェクト (JavaScript)
オートメーション オブジェクトへの参照を有効にして返します。  
  
 このオブジェクトはオートメーション オブジェクトのインスタンスを作成するだけのために使用し、メンバーはありません。  
  
> [!WARNING]
>  このオブジェクトは Microsoft 拡張機能であり、Internet Explorer でのみサポートされます。[!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリではサポートされません。  
  
## 構文  
  
```  
  
newObj = new ActiveXObject(servername.typename[, location])  
```  
  
## パラメーター  
 `newObj`  
 必須。  `ActiveXObject` を代入する変数名です。  
  
 `servername`  
 必須。  オブジェクトを提供するアプリケーションの名前です。  
  
 `typename`  
 必須。  作成するオブジェクトの型またはクラスです。  
  
 `location`  
 省略可能。  オブジェクトの作成先のネットワーク サーバーの名前。  
  
## 解説  
 オートメーション サーバーでは、少なくとも 1 種類のオブジェクトを提供します。  たとえば、ワードプロセッシング アプリケーションでは、アプリケーション オブジェクト、ドキュメント オブジェクト、およびツール バー オブジェクトが提供されます。  
  
 ホスト PC で `HKEY_CLASSES_ROOT` レジストリ キーの `servername.typename` の値を特定できる場合があります。  たとえば、インストールされているプログラムに応じて、次のような値を確認できます。  
  
-   Excel.Application  
  
-   Excel.Chart  
  
-   Scripting.FileSystemObject  
  
-   WScript.Shell  
  
-   Word.Document  
  
> [!IMPORTANT]
>  ActiveX オブジェクトでは、セキュリティ上の問題が発生する可能性があります。  `ActiveXObject` を使用するには、Internet Explorer で関連するセキュリティ ゾーンのセキュリティ設定を調整することが必要になる場合があります。  たとえば、\[ローカル イントラネット\] ゾーンでは、通常、\[スクリプトを実行しても安全だとマークされていない ActiveX コントロールの初期化とスクリプトの実行\] を有効にするようにカスタム設定を変更する必要があります。  
  
 オートメーション オブジェクトの使用可能なリファレンス ドキュメントがない場合、コードで使用できるオートメーション オブジェクトのメンバーを特定するには、[OLE\/COM オブジェクト ビューアー](http://msdn.microsoft.com/library/d0kh9f4c.aspx)などの COM オブジェクト ブラウザーを使用する必要があります。  
  
 オートメーション オブジェクトを作成するには、オブジェクト変数に新しい `ActiveXObject` を代入します。  
  
```javascript  
var ExcelApp = new ActiveXObject("Excel.Application");  
var ExcelSheet = new ActiveXObject("Excel.Sheet");  
```  
  
 このコードは、オブジェクト \(この場合は Microsoft Excel ワークシート\) を作成するアプリケーションを起動します。  オブジェクトが作成されると、定義したオブジェクト変数を使用してコード内で参照できます。  次の例では、オブジェクト変数 `ExcelSheet` と、Application オブジェクトや ActiveSheet.Cells コレクションなどの Excel のオブジェクトを使って、新しいオブジェクトのプロパティやメソッドにアクセスします。  
  
```javascript  
// Make Excel visible through the Application object.  
ExcelSheet.Application.Visible = true;  
// Place some text in the first cell of the sheet.  
ExcelSheet.ActiveSheet.Cells(1,1).Value = "This is column A, row 1";  
// Save the sheet.  
ExcelSheet.SaveAs("C:\\TEST.XLS");  
// Close Excel with the Quit method on the Application object.  
ExcelSheet.Application.Quit();  
```  
  
## 必要条件  
 Quirks、Internet Explorer 6 標準、Internet Explorer 7 標準、Internet Explorer 8 標準、Internet Explorer 9 標準、Internet Explorer 10 標準、および Internet Explorer 11 標準の各ドキュメント モードでサポートされます。  [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリではサポートされていません。  「[バージョン情報](../../javascript/reference/javascript-version-information.md)」を参照してください。  
  
> [!NOTE]
>  [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] 以降では、リモート サーバーにおける `ActiveXObject` の作成はサポートされません。  
  
## 参照  
 [GetObject 関数](../../javascript/reference/getobject-function-javascript.md)   
 [HTML5\/WCF の魔法を使用した一意の認証のサンプル アプリ](http://code.msdn.microsoft.com/Unique-Authentication-f32d2da0)