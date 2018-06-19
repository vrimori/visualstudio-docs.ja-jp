---
title: GetObject 関数 (JavaScript) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- GetObject
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- GetObject function
ms.assetid: 62efcdbc-8b86-491d-9000-ef38aa9942a9
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d8bad127a0f260395a1ec19f44ff2d495006024
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637462"
---
# <a name="getobject-function-javascript"></a>GetObject 関数 (JavaScript)
ファイルからオートメーション オブジェクトへの参照を返します。  
  
> [!NOTE]
>  Internet Explorer 9 (標準モードの場合) またはそれ以降は、この関数はサポートされていません。  
  
## <a name="syntax"></a>構文  
  
```  
GetObject([pathname] [, class])  
```  
  
## <a name="parameters"></a>パラメーター  
 `pathname`  
 省略可能です。 完全なパスと取得するオブジェクトを含むファイルの名前。 場合`pathname`を省略すると、`class`が必要です。  
  
 `class`  
 省略可能です。 オブジェクトのクラスです。  
  
 `class`引数の構文を使用する`appname.objectype`おり、これらの部分。  
  
 `appname`  
 必須です。 オブジェクトを提供するアプリケーションの名前。  
  
 `objectype`  
 必須です。 型またはオブジェクトのクラスを作成します。  
  
## <a name="remarks"></a>コメント  
 `GetObject`でサポートされない関数[!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)]またはそれ以降。  
  
 使用して、`GetObject`ファイルからオートメーション オブジェクトにアクセスする関数。 によって返されるオブジェクトを割り当てる`GetObject`オブジェクト変数にします。 例:  
  
```JavaScript  
var CADObject;  
CADObject = GetObject("C:\\CAD\\SCHEMA.CAD");  
```  
  
 このコードを実行すると、指定したに関連付けられたアプリケーション`pathname`開始されると、指定したファイル内のオブジェクトがアクティブ化します。 場合`pathname`は長さ 0 の文字列 ("")、`GetObject`指定した型の新しいオブジェクト インスタンスを返します。 場合、`pathname`引数を省略すると、`GetObject`指定した型の現在アクティブなオブジェクトを返します。 指定した型のオブジェクトが存在しない場合、エラーが発生します。  
  
 一部のアプリケーションでは、ファイルの一部をアクティブ化を行うことができます。 これを行うは、ファイル名の末尾に感嘆符 (!) を追加し、その後、アクティブ化するファイルの一部を識別する文字列にします。 この文字列を作成する方法については、オブジェクトを作成したアプリケーションのマニュアルを参照してください。  
  
 たとえば、描画アプリケーションでは、複数のレイヤーにファイルに格納されている描画があります。 次のコードを使用して記述すると、レイヤーをアクティブにでした`SCHEMA.CAD`:  
  
```JavaScript  
var LayerObject = GetObject("C:\\CAD\\SCHEMA.CAD!Layer3");  
```  
  
 オブジェクトのクラスを指定しない場合オートメーションどのアプリケーションを開始して、アクティブにするオブジェクトに基づいて決定、ファイル名を入力します。 ただし、一部のファイルでは、オブジェクトの 1 つ以上のクラスをサポートして可能性があります。 たとえば、図面は次の 3 つの異なる種類のオブジェクトをサポート可能性があります: アプリケーション オブジェクト、描画オブジェクトの場合、および同じファイルの一部であるすべてのツールバーのオブジェクト。 使用してアクティブ化するファイルのどのオブジェクトを指定する省略可能な`class`引数。 例:  
  
```JavaScript  
var MyObject;  
MyObject = GetObject("C:\\DRAWINGS\\SAMPLE.DRW", "FIGMENT.DRAWING");  
```  
  
 前の例で`FIGMENT`描画アプリケーションの名前を指定し、`DRAWING`はこれをサポートしているオブジェクトの種類の 1 つです。 オブジェクトがアクティブになると、参照するにはコードを定義して、オブジェクト変数を使用します。 オブジェクト変数を使用して新しいオブジェクトのプロパティおよびメソッドにアクセスする前の例で`MyObject`です。 例:  
  
```JavaScript  
MyObject.Line(9, 90);  
MyObject.InsertText(9, 100, "Hello, world.");  
MyObject.SaveAs("C:\\DRAWINGS\\SAMPLE.DRW");  
```  
  
> [!NOTE]
>  使用して、`GetObject`オブジェクトの現在のインスタンスがあるし、ファイルが既に読み込まれてを持つオブジェクトを作成する場合に機能します。 ファイルが読み込まれた現在のインスタンスがないと、オブジェクトの使用を開始したくない場合は、使用して、`ActiveXObject`オブジェクト。  
  
 オブジェクトがそれ自体を単独のオブジェクトとして登録している場合、オブジェクトの 1 つだけのインスタンスが作成、方法に関係なく何度も`ActiveXObject`を実行します。 単一インスタンス オブジェクトは、`GetObject`常に長さ 0 の文字列で呼び出されたときに、同じインスタンスを返します ("") 構文、およびその場合はエラーが発生、`pathname`引数を省略します。  
  
## <a name="requirements"></a>要件  
 各ドキュメント モードでサポートされる: Quirks、Internet Explorer 6 標準、Internet Explorer 7 標準、および Internet Explorer 8 標準です。 「 [バージョン情報](../../javascript/reference/javascript-version-information.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [ActiveXObject オブジェクト](../../javascript/reference/activexobject-object-javascript.md)