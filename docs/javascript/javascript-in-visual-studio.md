---
title: "Visual Studio の JavaScript | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f3eee13e-30e4-4bc1-81f5-058d7e379b75
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 77e7ce26df70e41e2328442454fe78c7a663f1f3
ms.openlocfilehash: de00ef86413571739446b61427c3a8e6c4680c06
ms.lasthandoff: 03/08/2017

---
# <a name="javascript-in-visual-studio"></a>Visual Studio の JavaScript
JavaScript は Visual Studio の第一級の言語です。 Visual Studio IDE で JavaScript コードを記述する場合に、ほとんどの標準的な編集補助機能 (コード スニペット、IntelliSense など) を使用できます。 多くの種類のアプリケーションやサービスの JavaScript コードを記述できます。  
  
 JavaScript 言語のリファレンス ドキュメントについては、「[JavaScript 言語リファレンス](https://docs.microsoft.com/scripting/javascript/javascript-language-reference)」を参照してください。
  
 特定のバージョンの Visual Studio、または特定の Visual Studio 拡張機能では、HTML および JavaScript を使用して特定の種類のアプリケーションとサービスを開発する必要があります。 次の一覧には詳細情報へのリンクがあります。  
  
-   Apache Cordova を使ってクロスプラットフォーム アプリを作成する方法については、「[Visual Studio Tools for Apache Cordova](https://docs.microsoft.com/visualstudio/cross-platform/tools-for-cordova/)」をご覧ください。  
  
-   Visual Studio で使うことができる JavaScript テクノロジへのリンクについては、「[JavaScript in Visual Studio](https://docs.microsoft.com/scripting/javascript/)」(Visual Studio での JavaScript) および「[Scripting Technologies](https://docs.microsoft.com/scripting/)」(スクリプト技術) のページをご覧ください。
  
 Visual Studio の JavaScript エディターでは IntelliSense をサポートしています。 詳細については、「[JavaScript IntelliSense](../ide/javascript-intellisense.md)」を参照してください。  
  
## <a name="whats-new-in-javascript"></a>JavaScript の新機能  
 JavaScript の新機能は、以下の表にリストされています。  
  
|特性|説明|  
|-------------|-----------------|  
|クラス|[クラス](http://msdn.microsoft.com/Library/bf45ebad-4678-4062-88df-55d32b603c69)の宣言をサポートする新しい構文です。|  
|Promise|[Promise](http://msdn.microsoft.com/Library/358ad98b-f7fa-448c-9ee0-ef1e2a45e9c6) を使用すると、より簡単で読みやすい非同期コーディングができます。 Promise コンストラクターは、`all` および `race` の各ユーティリティ メソッドと一緒にサポートされます。|  
|反復子|反復可能なオブジェクト (配列、配列に似たオブジェクト、および反復子を含む) を使用して反復処理を行い、それぞれの別個のプロパティの値に対して実行するステートメントを伴うカスタム反復フックを呼び出すことができるようになりました。 詳細については、「[反復子とジェネレーター](http://msdn.microsoft.com/Library/68ef5b2f-0349-492b-b557-73ff2a2f90cf)」を参照してください。 **注:** ジェネレーターはまだサポートされていません。|  
|アロー関数|アロー関数 (=>) は、レキシカルな `this` によるバインドの機能を持つ `function` キーワードの略式の構文を提供します。|  
|組み込みオブジェクトの新しいメソッド|[Array オブジェクト](http://msdn.microsoft.com/Library/08e5f552-0797-4b48-8164-609582fc18c9)、[Math オブジェクト](http://msdn.microsoft.com/Library/607b94cb-921c-43cd-b514-fdbc13aeced6)、[Number オブジェクト](http://msdn.microsoft.com/Library/76e87c37-cf6c-46cc-bafa-04be1fe3d78d)、[Object オブジェクト](http://msdn.microsoft.com/Library/d24ef8fc-217b-4828-94e1-19f72780bae0)、および [String オブジェクト](http://msdn.microsoft.com/Library/8063ecd5-5778-4e87-b985-b21420171914)の組み込みオブジェクトに、データの操作や確認に使用できる多くの新しいユーティリティ関数とプロパティが含まれています。|  
|オブジェクト リテラルの機能強化|オブジェクトにおいて、計算プロパティ、簡潔なメソッドの定義、および同じ名前の変数に値が初期化されるプロパティの略式の構文がサポートされるようになりました。 詳細については、「[オブジェクトの作成](http://msdn.microsoft.com/Library/58d1baa5-4fe8-4a56-a926-5b11765df704)」を参照してください。|  
|プロキシ|[プロキシ](http://msdn.microsoft.com/Library/2b89abee-04fa-47e6-9676-980016cff5f8)により、オブジェクトのカスタム動作を設定できます。|  
|rest パラメーター|rest パラメーターを使用すると、関数呼び出しの連続する引数を配列に変換できます。 詳細については、「[関数](http://msdn.microsoft.com/Library/e2a72b5a-3edd-43d8-95e8-91721b38c1c1)」を参照してください。|  
|spread 演算子|[spread 演算子](http://msdn.microsoft.com/Library/10263a4c-bd27-4d87-9917-fb4b6bf373db) (`…`) は、反復可能な式を個々の引数に展開します。 たとえば、`a.b(…array)` は `a.b.apply(a, array)` とほとんど同じです。|  
|シンボル|[Symbol](http://msdn.microsoft.com/Library/2ad059f1-4b7f-4758-882a-c74ce1283ab0) オブジェクトを使用して既存のオブジェクトにプロパティを追加すると、既存のオブジェクトのプロパティと干渉する可能性がなく、意図せずに可視になる可能性もなく、他のコードから整合性のない追加が実行される可能性もありません。|  
|テンプレート文字列|[テンプレート文字列](http://msdn.microsoft.com/Library/f2e525a5-b0fc-49c3-95a0-641788e5c12a)では、その文字列リテラルを式として評価し、そのリテラル文字列に連結することができます。|  
|Unicode の機能強化|Unicode のサポートが向上しました。 たとえば、エスケープ シーケンスの新しい形式では、アストラル コード ポイント (16 進数字&4; 桁を超えるコード ポイント) がサポートされます。 詳細については、「[特殊文字](http://msdn.microsoft.com/Library/3b38b1bd-1f0f-4748-b13e-55cab36fd126)」を参照してください。|  
|WeakSet|[WeakSet](http://msdn.microsoft.com/Library/f97e6e7c-d678-4e32-978e-d949a7cafa3a) は、他の場所から参照されていない場合にガベージ コレクションの対象となるオブジェクトのコレクションです。|
