---
title: "JavaScript の新機能 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 342b68ef-df93-48c4-81de-bdf6b6ce58d9
caps.latest.revision: 33
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 540d10958a7f2d406a6d70a633fc09a2cada8f41
ms.contentlocale: ja-jp
ms.lasthandoff: 08/11/2017

---
# <a name="what39s-new-in-javascript"></a>JavaScript の新機能
このドキュメントでは、[エッジ モード](http://blogs.msdn.com/b/ie/archive/2014/11/11/living-on-the-edge-our-next-step-in-interoperability.aspx)と [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)]および Windows Phone ストア アプリの両方でサポートされる JavaScript の新機能を示します。  
  
 エッジ モードではサポートされているが、[!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)] アプリでは非推奨である JavaScript の要素を確認する場合は、[バージョン情報](../javascript/reference/javascript-version-information.md)に関するページを参照してください。  
  
> [!IMPORTANT]
>  Visual Studio JavaScript エディターおよびその他の機能に関する情報を含む、JavaScript を使用する [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)]と Windows Phone ストア アプリの作成方法については、「[Visual Studio 2013 を使った Windows ストア アプリの開発](http://go.microsoft.com/fwlink/p/?LinkID=238263)」を参照してください。  
  
## <a name="new-features-in-javascript"></a>JavaScript の新機能  
  
|特性|説明|  
|-------------|-----------------|  
|クラス|[クラス](../javascript/reference/class-statement-javascript.md)の宣言をサポートする新しい構文です。|  
|Promise|[Promise](../javascript/reference/promise-object-javascript.md) を使用すると、より簡単で読みやすい非同期コーディングができます。 Promise コンストラクターは、`all` および `race` の各ユーティリティ メソッドと一緒にサポートされます。|  
|反復子|反復可能なオブジェクト (配列、配列に似たオブジェクト、および反復子を含む) を使用して反復処理を行い、それぞれの別個のプロパティの値に対して実行するステートメントを伴うカスタム反復フックを呼び出すことができるようになりました。 詳細については、「[反復子とジェネレーター](../javascript/advanced/iterators-and-generators-javascript.md)」を参照してください。 **注:** ジェネレーターはまだサポートされていません。|  
|アロー関数|アロー関数 (=>) は、レキシカルな `this` によるバインドの機能を持つ `function` キーワードの略式の構文を提供します。|  
|組み込みオブジェクトの新しいメソッド|[Array オブジェクト](../javascript/reference/array-object-javascript.md)、[Math オブジェクト](../javascript/reference/math-object-javascript.md)、[Number オブジェクト](../javascript/reference/number-object-javascript.md)、[Object オブジェクト](../javascript/reference/object-object-javascript.md)、および [String オブジェクト](../javascript/reference/string-object-javascript.md)の組み込みオブジェクトに、データの操作や確認に使用できる多くの新しいユーティリティ関数とプロパティが含まれています。|  
|オブジェクト リテラルの機能強化|オブジェクトにおいて、計算プロパティ、簡潔なメソッドの定義、および同じ名前の変数に値が初期化されるプロパティの略式の構文がサポートされるようになりました。 詳細については、「[オブジェクトの作成](../javascript/creating-objects-javascript.md)」を参照してください。|  
|プロキシ|[プロキシ](../javascript/reference/proxy-object-javascript.md)により、オブジェクトのカスタム動作を設定できます。|  
|rest パラメーター|rest パラメーターを使用すると、関数呼び出しの連続する引数を配列に変換できます。 詳細については、「[関数](../javascript/functions-javascript.md)」を参照してください。|  
|spread 演算子|[spread 演算子](../javascript/reference/spread-operator-decrement-dot-dot-dot-javascript.md) (`...`) は、反復可能な式を個々の引数に展開します。 たとえば、`a.b(...array)` は `a.b.apply(a, array)` とほとんど同じです。|  
|シンボル|[Symbol](../javascript/reference/symbol-object-javascript.md) オブジェクトを使用して既存のオブジェクトにプロパティを追加すると、既存のオブジェクトのプロパティと干渉する可能性がなく、意図せずに可視になる可能性もなく、他のコードから整合性のない追加が実行される可能性もありません。|  
|テンプレート文字列|[テンプレート文字列](../javascript/advanced/template-strings-javascript.md)では、その文字列リテラルを式として評価し、そのリテラル文字列に連結することができます。|  
|Unicode の機能強化|Unicode のサポートが向上しました。 たとえば、エスケープ シーケンスの新しい形式では、アストラル コード ポイント (16 進数字 4 桁を超えるコード ポイント) がサポートされます。 詳細については、「[特殊文字](../javascript/advanced/special-characters-javascript.md)」を参照してください。|  
|WeakSet|[WeakSet](../javascript/reference/weakset-object-javascript.md) は、他の場所から参照されていない場合にガベージ コレクションの対象となるオブジェクトのコレクションです。|  
  
## <a name="see-also"></a>関連項目  
 [JavaScript 言語リファレンス](../javascript/javascript-language-reference.md)
