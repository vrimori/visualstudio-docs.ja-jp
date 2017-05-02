---
title: "IDispatchEx インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDispatchEx インターフェイス"
  - "IDispatchEx インターフェイス, IDispatchEx の概要"
ms.assetid: 37a3303f-f78e-4b5b-aac8-b836c92819de
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IDispatchEx インターフェイス
`IDispatchEx`の `IDispatch` のインターフェイスの拡張子は、スクリプト言語などの動的言語に適した機能をサポートしています。  ここでは `IDispatchEx` のインターフェイス自体、`IDispatch` と `IDispatchEx`の違い、および拡張機能の根拠について説明します。  リーダーは `IDispatch` を理解して、`IDispatch` ドキュメントにアクセスできると想定されます。  
  
## 解説  
 `IDispatch` は、Microsoft Visual Basic では、基本的に開発されました。  `IDispatch` の主要な制限は、オブジェクトが静的であると仮定します。  つまり、オブジェクトが実行時に変更されないので、型情報は、コンパイル時に完全に記述できます。  Visual Basic Scripting Edition \(VBScript などのスクリプト言語に、動的 HTML など [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] とオブジェクト モデルは動的ランタイムのモデルは、より柔軟なインターフェイスを要求できます。  
  
 `IDispatchEx` は、スクリプト言語などの動的遅延バインディング言語に適した `IDispatch`、その拡張子のすべてのサービスを提供するために開発されました。  `IDispatch` によって提供される機能を超える `IDispatchEx` の追加機能は次のとおりです:  
  
-   expando オブジェクト \(「」\) に新しいメンバーを使用します `fdexNameEnsure` —フラグを持つ `GetDispID` を追加します。  
  
-   オブジェクトまたはメンバーの使用 `DeleteMemberByName``DeleteMemberByDispID`を削除します。  
  
-   大文字と小文字を区別するディスパッチ使用 `fdexNameCaseSensitive` 操作または `fdexNameCaseInsensitive`。  
  
-   暗黙の使用 `fdexNameImplicit`名前を持つメンバーを検索します。  
  
-   オブジェクトを使用 `GetNextDispID`の DISPID を列挙します。  
  
-   任意の要素名を使用 `GetMemberName`にマップします。  
  
-   オブジェクトのメンバー使用 `GetMemberProperties`のプロパティを取得します。  
  
-   DISPATCH\_METHOD の `this` ポインターの使用 `InvokeEx` を持つメソッドを呼び出します。  
  
-   オブジェクトを使用 `GetNameSpaceParent`の名前空間の親を取得するには、名前空間の概念をサポートするブラウザーを許可します。  
  
 `IDispatchEx` をサポートするオブジェクトは、下位互換性のための `IDispatch` をサポートする場合があります。  `IDispatchEx` をサポートするオブジェクトの動的な特性にオブジェクトの `IDispatch` のインターフェイスの数に影響を及ぼします。  たとえば、`IDispatch` は、次の前提とします:  
  
-   メンバー、およびパラメーターの DISPID がオブジェクトの有効期間に一定に置かれます。  これはクライアントが DISPID を一度取得し、後で使用できるようにキャッシュすることもできます。  
  
 `IDispatchEx` がメンバーの追加および削除できるので、有効な任意のセットは、一定に残りません。  ただし、`IDispatchEx` は DISPID とメンバーの名前との間のマップが設定しておく必要があります。  これは、メンバーが削除されると、を意味します:  
  
-   DISPID は同じ名前のメンバーが作成されるまで再利用することはできません。  
  
-   DISPID は `GetNextDispID`に対して有効である必要があります。  
  
-   DISPID は、メソッドが削除されるように、メンバーを確認し、適切なエラー コードを返す必要があります `IDispatchEx` か `IDispatch` によって適切に受け入れられる \(通常は S\_FALSE DISP\_E\_MEMBERNOTFOUND または\)。  
  
## 例  
 関数のテスト\(\) [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] このコードは、次の処理を行います :  
  
-   新しいオブジェクトを `Object` のコンストラクターによる作成し、可変 Obj に新しいオブジェクトへのポインターを割り当てます。  
  
-   オブジェクトで Elem という名前の新しい要素を作成し、この要素に関数ポインターに猫を割り当てます。  
  
-   この関数を呼び出します。  これがメソッドとして呼び出されるため、`this` のポインターはオブジェクト Obj を参照します。  関数は、オブジェクト、バーに新しい要素を追加します。  
  
 HTML コードは次のとおりです:  
  
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
  
 この同じ Web ページに設定されたコントロールはブラウザーのスクリプト エンジンにディスパッチのポインターを取得できます。  コントロールは、関数テスト \(\) を実行できます:  
  
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
  
 コントロールからコードは、テスト [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 関数 `test()`と、同じです。  これらのディスパッチ呼び出しが [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] の実行中に行われるエンジンは、エンジンの状態をに変更する:  
  
-   `GetDispID()`を使用して猫の関数のやにディスパッチのポインターを取得します。  
  
-   `GetDispID()`を使用してオブジェクトの関数にディスパッチのポインターを取得します。  
  
-   オブジェクトを `InvokeEx()` のオブジェクトの関数を呼び出して、構築し、新しく生成されたオブジェクトにディスパッチのポインターを取得します。  
  
-   `fdexNameEnsure` フラグを持つ `GetDispID()` を使用して新しい要素、オブジェクトの Elem を作成します。  
  
-   `InvokeEx()`を使用して要素に猫にディスパッチ ポインターを設定します。  
  
-   `InvokeEx()` を呼び出し、`this` のポインターとして構築されたオブジェクトにディスパッチのポインターを渡すことによってメソッドとして猫にディスパッチ ポインターを呼び出します。  
  
-   猫のメソッドは、新しい要素 `this` の現在のオブジェクトのバーを作成します。  
  
-   新しい要素、バーが構築されたオブジェクトで `GetNextDispID()`、を使用して要素を列挙して作成されたことを確認します。  
  
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
  
## メソッド  
 [IDispatchEx メソッド](../../winscript/reference/idispatchex-methods.md)