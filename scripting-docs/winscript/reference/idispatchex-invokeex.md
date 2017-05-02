---
title: "IDispatchEx::InvokeEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.InvokeEx
apilocation: scrobj.dll
helpviewer_keywords: 
  - "InvokeEx メソッド"
ms.assetid: d90783e6-4b89-4423-8a56-a9c8b4b2c813
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDispatchEx::InvokeEx
`IDispatchEx` のオブジェクトによって公開されるプロパティとメソッドにアクセスできます。  
  
## 構文  
  
```  
HRESULT InvokeEx(  
   DISPID id,  
   LCID lcid,  
   WORD wFlags,  
   DISPARAMS *pdp,  
   VARIANT *pVarRes,   
   EXCEPINFO *pei,   
   IServiceProvider *pspCaller   
);  
```  
  
#### パラメーター  
 `id`  
 メンバーを識別します。  ディスパッチ ID を取得または `GetNextDispID` 使用 `GetDispID`。  
  
 `lcid`  
 引数を解釈する対象のロケール コンテキスト。  `lcid` は `InvokeEx` にオブジェクトがロケール固有の引数を解釈するために渡されます。  
  
 `wFlags`  
 `wFlags` の有効な値は次のとおりです:  
  
 DISPATCH\_PROPERTYGET &#124; DISPATCH\_METHOD &#124; DISPATCH\_PROPERTYPUT &#124; DISPATCH\_PROPERTYPUTREF &#124; DISPATCH\_CONSTRUCT  
  
 `InvokeEx` の呼び出しのコンテキストを表すフラグ:  
  
|値|説明|  
|-------|--------|  
|DISPATCH\_METHOD|メンバーは、メソッドとして起動されます。  プロパティの名前が同じであり、これ DISPATCH\_PROPERTYGET フラグが設定されている場合があります \( `IDispatch`で定義\) です。|  
|DISPATCH\_PROPERTYGET|メンバーには、プロパティやデータ メンバーとして取得されます \( `IDispatch`で定義\) です。|  
|DISPATCH\_PROPERTYPUT|メンバーは、プロパティやデータ メンバーとして変更されます \( `IDispatch`で定義\) です。|  
|DISPATCH\_PROPERTYPUTREF|メンバーは、値の代入ではなく参照の割り当てによって変更されます。  このフラグは、プロパティがオブジェクトへの参照を受け入れる場合のみ有効です \( `IDispatch`で定義\) です。|  
|DISPATCH\_CONSTRUCT|メンバーは、コンストラクターとして使用されます。   \(これは `IDispatchEx`で定義されている新しい値\)。  `wFlags` の有効な値は次のとおりです:<br /><br /> DISPATCH\_PROPERTYGET DISPATCH\_METHOD DISPATCH\_PROPERTYPUT DISPATCH\_PROPERTYPUTREF DISPATCH\_CONSTRUCT|  
  
 `pdp`  
 引数の配列、名前付き引数の DISPID の配列、配列内の要素数のカウントを格納している構造体へのポインター。  DISPPARAMS の構造の詳細については、`IDispatch` ドキュメントを参照してください。  
  
 `pVarRes`  
 呼び出し元が結果を期待する結果が格納されている場所または null へのポインター。  この引数は DISPATCH\_PROPERTYPUT か DISPATCH\_PROPERTYPUTREF を指定した場合は無視されます。  
  
 `pei`  
 例外情報を格納する構造体へのポインター。  この構造は `DISP_E_EXCEPTION` が返されると指定してください。  null にすることができます。  `EXCEPINFO` の構造の詳細については、`IDispatch` ドキュメントを参照してください。  
  
 `pspCaller`  
 オブジェクトが呼び出し元からサービスを取得できるようにする呼び出し元が提供するサービス プロバイダー オブジェクトへのポインター。  null にすることができます。  
  
 `IDispatchEx::InvokeEx` は `IDispatch::Invoke` と同じ機能がすべて用意し、いくつかの拡張子を追加します:  
  
|||  
|-|-|  
|DISPATCH\_CONSTRUCT|項目がコンストラクターとして使用されていることを示します。|  
|`pspCaller`|`pspCaller` は、呼び出し元が提供するサービスのオブジェクトへのアクセスを許可します。  特定のサービスで呼び出し元自身で処理されるか、または呼び出しチェーンの上位の呼び出し元のように代入される場合があります。  たとえば、ブラウザー内のスクリプト エンジンが外部オブジェクトに `InvokeEx` の呼び出しを行う場合、オブジェクトはスクリプト エンジンまたはブラウザーからサービスを取得するに `pspCaller` チェーンをたどってできます。   \(呼び出しチェーンがコンテナーのチェーンまたはサイトのチェーンと呼ばれる作成のチェーンまたはとは異なる注意してください。  チェーンは `IObjectWithSite`の作成などの機構を通じて使用できる場合があります\)。|  
|`this` ポインター|DISPATCH\_METHOD `wFlags`がに設定されている場合、この値「」の「名前付きパラメーター」である場合があります。  DISPID は DISPID\_THIS であり、最初の名前付きパラメーターである必要があります。|  
  
 `IDispatch::Invoke` の `riid` の未使用のパラメーターが削除されました。  
  
 `IDispatch::Invoke` の `puArgArr` のパラメーターが削除されました。  
  
 次の例については、のドキュメントを参照してください `IDispatch::Invoke` :  
  
 「引数なしでメソッドを呼び出します」。  
  
 「get プロパティを」  
  
 「パラメーター」を渡します  
  
 「インデックス付きプロパティを」  
  
 「例外を発生時に呼び出します」。  
  
 「戻る」エラー  
  
## 戻り値  
 次の値の場合: 1  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|DISP\_E\_BADPARAMCOUNT|DISPPARAMS に指定された要素の数は、メソッドまたはプロパティが受け取る引数の数とは異なります。|  
|DISP\_E\_BADVARTYPE|`rgvarg` 引数の 1 つが有効なさまざまな型ではありません。|  
|DISP\_E\_EXCEPTION|アプリケーションは例外を発生させる必要があります。  この場合、`pei` で渡された構造が表示されます。|  
|DISP\_E\_MEMBERNOTFOUND|要求されたメンバーが存在しない、または `InvokeEx` の呼び出しは読み取り専用のプロパティの値を設定しようとしました。|  
|DISP\_E\_NONAMEDARGS|この `IDispatch` の実装は名前付き引数はサポートされていません。|  
|DISP\_E\_OVERFLOW|`rgvarg` 引数の 1 つがは、指定された型に変換できません。|  
|DISP\_E\_PARAMNOTFOUND|パラメーターの DISPID の 1 つが、メソッドのパラメーターに対応しません。|  
|DISP\_E\_TYPEMISMATCH|一つ以上の引数に変換できませんでした。|  
|DISP\_E\_UNKNOWNLCID|開始するメンバーは LCID に従って文字列引数を解釈し、LCID は検証されません。  LCID が引数を解釈するために必要ない場合、このエラーを返す必要はありません。|  
|DISP\_E\_PARAMNOTOPTIONAL|必須パラメーターが省略されています。|  
  
## 使用例  
  
```  
VARIANT var;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
   DISPPARAMS dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
   {  
      pdex->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
   }  
```  
  
## 参照  
 [IDispatchEx インターフェイス](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)