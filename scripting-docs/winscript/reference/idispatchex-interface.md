---
title: "IDispatchEx インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDispatchEx interface, about IDispatchEx
- IDispatchEx interface
ms.assetid: 37a3303f-f78e-4b5b-aac8-b836c92819de
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a100a193f5e3abcb076fb8aaf3d64a0d0c38833
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchex-interface"></a>IDispatchEx インターフェイス
`IDispatchEx`での拡張機能、`IDispatch`インターフェイスをサポートする機能に適したスクリプト言語などの動的言語。 このセクションの内容について説明します、`IDispatchEx`インターフェイス自体の間の相違点`IDispatch`と`IDispatchEx`、および拡張機能の論理的根拠は、します。 リーダーが慣れていることを想定して`IDispatch`にアクセスし、`IDispatch`ドキュメント。  
  
## <a name="remarks"></a>コメント  
 `IDispatch`開発された基本的には Microsoft Visual Basic のです。 主な制限`IDispatch`オブジェクトが静的であることと見なされます。 つまり、オブジェクトは、実行時に変更しない限り後、型情報を完全に記述できるにコンパイル時にします。 Visual Basic Scripting Edition (VBScript) などのスクリプト言語内にあるランタイム モデルを動的と[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]とダイナミック HTML がより柔軟なインターフェイスを必要とするなど、オブジェクトをモデル化します。  
  
 `IDispatchEx`すべてのサービスを提供するために開発された`IDispatch`スクリプト言語より動的の遅延バインディングされた言語に対応する一部の拡張機能とします。 他の機能`IDispatchEx`で提供されていない`IDispatch`は。  
  
-   オブジェクト ("expando") に新しいメンバーを追加: 使用`GetDispID`で、`fdexNameEnsure`フラグ。  
  
-   オブジェクトのメンバーを削除: 使用`DeleteMemberByName`または`DeleteMemberByDispID`です。  
  
-   大文字小文字を区別ディスパッチ操作-使用`fdexNameCaseSensitive`または`fdexNameCaseInsensitive`です。  
  
-   暗黙的な名前を持つメンバーの検索などを使用して`fdexNameImplicit`です。  
  
-   オブジェクトの Dispid の列挙-使用`GetNextDispID`です。  
  
-   DISPID からのマップを要素名-使用`GetMemberName`です。  
  
-   オブジェクトのメンバーのプロパティを取得: を使用して`GetMemberProperties`です。  
  
-   メソッドを呼び出すと`this`ポインターなどを使用して`InvokeEx`DISPATCH_METHOD とします。  
  
-   オブジェクトの名前空間の親を取得する名前空間の概念をサポートするブラウザーを許可する-使用`GetNameSpaceParent`です。  
  
 オブジェクトをサポートする`IDispatchEx`サポートする場合も`IDispatch`旧バージョンとの互換性のためです。 サポートするオブジェクトの動的な性質`IDispatchEx`がいくつかの影響、`IDispatch`それらのオブジェクトのインターフェイスです。 たとえば、`IDispatch`次が想定します。  
  
-   メンバーおよびパラメーター Dispid を一定に保つオブジェクトの有効期間。 これにより、クライアントに Dispid を一度入手したら、それらを後で使用できるキャッシュできます。  
  
 `IDispatchEx`によりの追加と削除、一連の有効な Dispid メンバー一定していません。 ただし、 `IDispatchEx` DISPID とメンバー名の間のマッピングが一定に保つことが必要です。 つまり、メンバーを削除する場合。  
  
-   DISPID は、同じ名前のメンバーが作成されるまで再利用できません。  
  
-   DISPID は有効でなければなりません`GetNextDispID`です。  
  
-   DISPID は、のいずれかによって正常に受け入れられる必要があります、`IDispatch`または`IDispatchEx`メソッド-削除済みとして、メンバーを認識し、適切なエラー コード (通常 DISP_E_MEMBERNOTFOUND または S_FALSE) を返すする必要があります。  
  
## <a name="examples"></a>例  
 これは、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]関数 test() 内のコードは次を実行します。  
  
-   呼び出して、新しいオブジェクトを作成、`Object`コンス トラクターと、ポインター変数オブジェクトに新しいオブジェクトに割り当てます  
  
-   Elem をという名前のオブジェクトに新しい要素を作成し、この要素に関数 cat へのポインターを割り当てます。  
  
-   この関数を呼び出します。 メソッドとして呼び出されたため、`this`ポインターがオブジェクトのオブジェクトを参照関数は、新しい要素を追加するオブジェクトへのバーです。  
  
 完全な HTML コードは次のとおりです。  
  
```  
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
  
 この Web ページに配置されるコントロールは、ブラウザーから、スクリプト エンジンにディスパッチのポインターを取得可能性があります。 コントロールは、関数 test() を実装し、でした。  
  
```  
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
  
 コントロールからのコード、テストと同じですが、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]関数`test()`です。 実行中にこれらのディスパッチ呼び出しが行われることに注意してください[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]エンジンし、エンジンの状態を変更します。  
  
-   Cat 関数を使用してへのディスパッチ ポインターを取得`GetDispID()`です。  
  
-   ディスパッチへのポインター、関数を使用してオブジェクトを取得`GetDispID()`です。  
  
-   オブジェクトを持つ関数を呼び出すことによってオブジェクトを構築`InvokeEx()`し、新しく構築されたオブジェクトへのディスパッチ ポインターを取得します。  
  
-   オブジェクトを使用して、Elem,、新しい要素を作成`GetDispID()`で、`fdexNameEnsure`フラグ。  
  
-   要素を使用して、cat にディスパッチ カーソルを置きます`InvokeEx()`です。  
  
-   Cat へのディスパッチ ポインターをメソッドとして呼び出すことによって呼び出す`InvokeEx()`をディスパッチ ポインターとして構築されたオブジェクトに渡すと、`this`ポインター。  
  
-   Cat メソッドは、新しい要素を作成します。 現在のバー`this`オブジェクト。  
  
-   確認、新しい要素では、横棒グラフ、によって作成された構築されたオブジェクトを使用して要素を列挙して`GetNextDispID()`です。  
  
 テストのコントロールのコード:  
  
```  
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