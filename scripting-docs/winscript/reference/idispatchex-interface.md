---
title: IDispatchEx インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDispatchEx interface, about IDispatchEx
- IDispatchEx interface
ms.assetid: 37a3303f-f78e-4b5b-aac8-b836c92819de
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a59f30c5b42301d29b73a4a079837423614da49
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087582"
---
# <a name="idispatchex-interface"></a>IDispatchEx インターフェイス
`IDispatchEx`での拡張機能、`IDispatch`スクリプト言語などの動的言語に適切なインターフェイスをサポートする機能。 このセクションについて説明します、`IDispatchEx`インターフェイス自体の間の相違点`IDispatch`と`IDispatchEx`、拡張機能の"the rationale"とします。 リーダーについて理解していることが予想`IDispatch`にアクセスし、`IDispatch`ドキュメント。  
  
## <a name="remarks"></a>Remarks  
 `IDispatch` 開発 for Microsoft Visual Basic では基本的に。 主な制限`IDispatch`オブジェクトを静的にすると見なされます。 つまり、オブジェクトは実行時に変化がないため型情報完全に記述できるにコンパイル時にします。 Visual Basic Scripting Edition (VBScript) などのスクリプト言語内にあるランタイム モデルを動的と[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]オブジェクト モデルなど、動的 HTML がより柔軟なインターフェイスを必要とします。  
  
 `IDispatchEx` すべてのサービスを提供するために開発された`IDispatch`より動的な遅延バインディングなどの言語のスクリプト言語に該当する一部の拡張機能とします。 追加機能`IDispatchEx`によって提供されるもの以外`IDispatch`は。  
  
- オブジェクト ("expando") に新しいメンバーを追加-を使用して、`GetDispID`で、`fdexNameEnsure`フラグ。  
  
- オブジェクトのメンバーの削除: を使用して、`DeleteMemberByName`または`DeleteMemberByDispID`します。  
  
- 大文字小文字を区別するディスパッチ操作-使用`fdexNameCaseSensitive`または`fdexNameCaseInsensitive`します。  
  
- 暗黙的な名前を持つメンバーの検索などを使用して、`fdexNameImplicit`します。  
  
- オブジェクトの Dispid の列挙-を使用して、`GetNextDispID`します。  
  
- 要素名に DISPID からマップ: を使用して、`GetMemberName`します。  
  
- オブジェクトのメンバーのプロパティを取得: を使用して、`GetMemberProperties`します。  
  
- メソッドを呼び出すと`this`ポインターなどを使用して、 `InvokeEx` DISPATCH_METHOD とします。  
  
- オブジェクトの名前空間の親を取得する名前空間の概念をサポートするブラウザーを許可する: を使用して、`GetNameSpaceParent`します。  
  
  オブジェクトをサポートする`IDispatchEx`サポートする場合も`IDispatch`旧バージョンとの互換性のためです。 サポートするオブジェクトの動的な性質`IDispatchEx`いくつかに影響があります、`IDispatch`これらのオブジェクトのインターフェイス。 たとえば、`IDispatch`次想定しています。  
  
- メンバーとパラメーター Dispid を一定に保つオブジェクトの有効期間。 これにより、クライアントを 1 回 Dispid を取得し、後で使用できるキャッシュします。  
  
  `IDispatchEx`追加と削除、有効な Dispid のセットのメンバーの状態が解除される定数を使用します。 ただし、 `IDispatchEx` DISPID とメンバー名の間のマッピングを一定に保つことが必要です。 つまり、メンバーが削除された場合。  
  
- DISPID は、同じ名前のメンバーが作成されるまで再利用することはできません。  
  
- DISPID の有効なままにする必要があります`GetNextDispID`します。  
  
- いずれかで、DISPID を適切に同意する必要が、`IDispatch`または`IDispatchEx`メソッド-削除済みとしては、メンバーを認識し、適切なエラー コード (通常は DISP_E_MEMBERNOTFOUND または S_FALSE) を返すする必要があります。  
  
## <a name="examples"></a>使用例  
 これは、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]関数 test() 内のコードは、次を実行します。  
  
- 呼び出して新しいオブジェクトを作成、`Object`コンス トラクターと、新しいオブジェクトを変数オブジェクトにポインターを割り当てます  
  
- オブジェクトの要素をという名前の新しい要素を作成し、関数 cat へのポインターをこの要素に割り当てます。  
  
- この関数を呼び出します。 メソッドとして呼び出されたため、`this`ポインターによって参照されたオブジェクト obj.関数は、新しい要素を追加しますオブジェクトへのバー。  
  
  完全な HTML コードに示します。  
  
```html
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
  
function test()  
{  
   // Construct new object  
   Obj = new Object();  
  
   // Create new element and assign function pointer  
   Obj.Elem = cat;  
  
   // Call Elem method ("this" == Obj)  
   Obj.Elem();  
  
   // Obj.Bar now exists  
}  
test();  
</script>  
</body>  
</html>  
```  
  
 この同じ Web ページ上のコントロールは、ブラウザーから、スクリプト エンジンにディスパッチのポインターを取得でした。 コントロールは、関数 test() を実装しでした。  
  
```html
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
</script>  
<object id="test" <CLASSID="CLSID:9417DB5D-FA2A-11D0-8CB3-00C04FC2B085">>  
</object>  
</body>  
</html>  
```  
  
 コントロールからのコード、テストと同じですが、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]関数`test()`します。 これらのディスパッチ呼び出しが実行中に行われることに注意してください。[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]エンジンとエンジンの状態を変更します。  
  
- Cat 関数を使用するディスパッチ ポインターを取得`GetDispID()`します。  
  
- オブジェクトの関数を使用するディスパッチ ポインターを取得`GetDispID()`します。  
  
- 使用して、オブジェクト関数を呼び出すことによって、オブジェクトを構築`InvokeEx()`新しく構築されたオブジェクトへのディスパッチ ポインターを取得します。  
  
- オブジェクトを使用して、新しい要素を Elem, を作成します。`GetDispID()`で、`fdexNameEnsure`フラグ。  
  
- 要素を使用して、cat にディスパッチを置きます`InvokeEx()`します。  
  
- Cat へのディスパッチのポインターをメソッドとして呼び出すことによって呼び出し`InvokeEx()`ディスパッチ ポインターとして構築されたオブジェクトを渡すと、`this`ポインター。  
  
- Cat メソッドは、新しい要素を作成します。 バーの現在`this`オブジェクト。  
  
- 検証が行われます新しい要素をバーが作成された構築されたオブジェクトを使用して要素を列挙して`GetNextDispID()`します。  
  
  テストのコントロールのコード:  
  
```cpp
   BOOL test(IDispatchEx *pdexScript)  
   {  
      HRESULT hr;  
      VARIANT var;  
      DISPID dispid, putid;  
      BOOL retval = FALSE;  
      BSTR bstrName = NULL;  
      IDispatch   *pdispObj = NULL, *pdispCat = NULL;  
      IDispatchEx *pdexObj = NULL;  
      DISPPARAMS dispparams, dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
      // Get dispatch pointer for "cat"  
      bstrName = SysAllocString(OLESTR("cat"));  
         if (bstrName == NULL) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispCat = var.pdispVal;  
  
      // Create object by calling "Object" constructor  
      bstrName = SysAllocString(OLESTR("Object"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_CONSTRUCT, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispObj = var.pdispVal;  
      hr = pdispObj->QueryInterface(IID_IDispatchEx, (void **)&pdexObj);  
         if (FAILED(hr)) goto LDone;  
  
      // Create new element in object  
      bstrName = SysAllocString(OLESTR("Elem"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexObj->GetDispID(bstrName, fdexNameEnsure, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
  
      // Assign "cat" dispatch pointer to element  
      putid = DISPID_PROPERTYPUT;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispCat;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYPUTREF, &dispparams,  
         NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Invoke method with "this" pointer  
      putid = DISPID_THIS;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispObj;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_METHOD, &dispparams,  
            NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Confirm that new element "Bar" is in object  
      hr = pdexObj->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);  
      while (hr == NOERROR)  
      {  
            hr = pdexObj->GetMemberName(dispid, &bstrName);  
            if (FAILED(hr)) goto LDone;  
            retval = !wcscmp(bstrName, OLESTR("Bar"));  
            SysFreeString(bstrName);  
            bstrName = NULL;  
            if (retval) goto LDone;  
         hr = pdexObj->GetNextDispID(fdexEnumAll, dispid, &dispid);  
      }  
LDone:  
   SysFreeString(bstrName);  
   if (pdispCat != NULL)  
      pdispCat->Release();  
   if (pdispObj != NULL)  
      pdispObj->Release();  
   if (pdexObj != NULL)  
      pdexObj->Release();  
  
   return retval;  
   }  
```  
  
## <a name="methods"></a>メソッド  
 [IDispatchEx メソッド](../../winscript/reference/idispatchex-methods.md)