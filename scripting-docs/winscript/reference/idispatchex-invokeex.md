---
title: "IDispatchEx::InvokeEx |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDispatchEx.InvokeEx
apilocation:
- scrobj.dll
helpviewer_keywords:
- InvokeEx method
ms.assetid: d90783e6-4b89-4423-8a56-a9c8b4b2c813
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6302228b110e2b0a6296190079bf60b3d92980bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexinvokeex"></a>IDispatchEx::InvokeEx
プロパティとによって公開されるメソッドにアクセスできるように、`IDispatchEx`オブジェクト。  
  
## <a name="syntax"></a>構文  
  
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
  
#### <a name="parameters"></a>パラメーター  
 `id`  
 メンバーを識別します。 使用して`GetDispID`または`GetNextDispID`ディスパッチ識別子を取得します。  
  
 `lcid`  
 引数を解釈する対象のロケール コンテキスト。 `lcid`に渡される`InvokeEx`ロケールに固有の引数を解釈するオブジェクトを許可します。  
  
 `wFlags`  
 値は、法的`wFlags`は。  
  
 DISPATCH_PROPERTYGET &#124;です。DISPATCH_METHOD &#124;です。DISPATCH_PROPERTYPUT &#124;です。DISPATCH_PROPERTYPUTREF &#124;です。DISPATCH_CONSTRUCT  
  
 コンテキストを記述するフラグ、`InvokeEx`呼び出し。  
  
|値|説明|  
|-----------|-------------|  
|DISPATCH_METHOD|メソッドとメンバーが呼び出されます。 これと DISPATCH_PROPERTYGET フラグを設定することがあります、プロパティには、同じ名前が付いている場合 (によって定義された`IDispatch`)。|  
|DISPATCH_PROPERTYGET|メンバーは、プロパティまたはデータ メンバーとして取得 (によって定義された`IDispatch`)。|  
|DISPATCH_PROPERTYPUT|メンバーが変更されたプロパティまたはデータ メンバー (によって定義された`IDispatch`)。|  
|DISPATCH_PROPERTYPUTREF|値の代入ではなく、参照の割り当てによって、メンバーが変更されます。 このフラグが有効では、プロパティがオブジェクトへの参照を受け入れる場合にのみ (によって定義された`IDispatch`)。|  
|DISPATCH_CONSTRUCT|メンバーは、コンス トラクターとして使用されています。 (これは、新しい値によって定義された`IDispatchEx`)。 値は、法的`wFlags`は。<br /><br /> DISPATCH_PROPERTYGET DISPATCH_METHOD DISPATCH_PROPERTYPUT DISPATCH_PROPERTYPUTREF DISPATCH_CONSTRUCT|  
  
 `pdp`  
 引数の配列、名前付き引数の DISPID の配列、配列内の要素数のカウントを格納している構造体へのポインター。 参照してください、 `IDispatch` DISPPARAMS 構造体の詳細についてはドキュメントです。  
  
 `pVarRes`  
 結果が保存または呼び出し元が結果を持たない場合は Null にする場所へのポインター。 DISPATCH_PROPERTYPUT または DISPATCH_PROPERTYPUTREF が指定されている場合、この引数は無視されます。  
  
 `pei`  
 例外情報を格納する構造体へのポインター。 この構造体の場合に塗りつぶしが必要`DISP_E_EXCEPTION`が返されます。 Null にすることができます。 参照してください、`IDispatch`ドキュメントの完全な説明を`EXCEPINFO`構造体。  
  
 `pspCaller`  
 により、オブジェクトがサービスを取得する呼び出し元から呼び出し元によって指定されたサービス プロバイダー オブジェクトへのポインター。 Null にすることができます。  
  
 `IDispatchEx::InvokeEx`同じ機能をすべて提供`IDispatch::Invoke`し、一部の拡張機能を追加します。  
  
|||  
|-|-|  
|DISPATCH_CONSTRUCT|コンス トラクターとして、項目を使用していることを示します。|  
|`pspCaller`|`pspCaller`呼び出し元が提供するサービス オブジェクトへのアクセス許可。 特定のサービス自体、呼び出し元によって処理されるまたは呼び出しチェーンの上にさらに呼び出し元に委任します。 たとえば、内のスクリプト エンジンの場合、ブラウザーで、`InvokeEx`外部オブジェクト、オブジェクトへの呼び出しは、`pspCaller`チェーンをスクリプト エンジンまたはブラウザーからサービスを取得します。 (呼び出しチェーンがない作成チェーンと同じ-コンテナー チェーンまたはサイト チェーンとも呼ばれます。 作成チェーンできる場合がありますの他のメカニズムによってなど`IObjectWithSite`)。|  
|`this` ポインター|設定すると DISPATCH_METHOD が`wFlags`、"this"値「名前付きパラメーター」である可能性があります。 DISPID は DISPID_THIS であり、最初の名前付きパラメーターがあります。|  
  
 未使用`riid`パラメーター`IDispatch::Invoke`は削除されました。  
  
 `puArgArr`パラメーター`IDispatch::Invoke`は削除されました。  
  
 参照してください、`IDispatch::Invoke`例については、次のドキュメント。  
  
 「引数なしでのメソッドを呼び出すと」  
  
 「を取得するプロパティを設定」  
  
 「パラメーターの引き渡し」  
  
 [インデックスのプロパティ]  
  
 「Invoke 中に例外を発生させる」  
  
 「エラーを返す」  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|DISP_E_BADPARAMCOUNT|DISPPARAMS に提供される要素の数とは異なりますメソッドまたはプロパティで受け入れられる引数の数です。|  
|DISP_E_BADVARTYPE|引数のいずれかの`rgvarg`は無効な variant 型ではありません。|  
|DISP_E_EXCEPTION|アプリケーションは、例外を発生させる必要があります。 ここでは、構造体渡された`pei`に入力する必要があります。|  
|DISP_E_MEMBERNOTFOUND|要求されたメンバーが存在しないかへの呼び出し`InvokeEx`読み取り専用プロパティの値を設定しようとしています。|  
|DISP_E_NONAMEDARGS|この実装`IDispatch`名前付き引数をサポートしていません。|  
|DISP_E_OVERFLOW|引数のいずれかの`rgvarg`指定された型には強制されませんでした。|  
|DISP_E_PARAMNOTFOUND|Dispid パラメーターの 1 つは、メソッドのパラメーターに対応していません。|  
|DISP_E_TYPEMISMATCH|1 つ以上の引数は、強制されませんでした。|  
|DISP_E_UNKNOWNLCID|呼び出されているメンバーは、LCID に従って文字列引数を解釈し、LCID は認識されません。 LCID が引数を解釈する必要がない場合、このエラーが返されません必要があります。|  
|DISP_E_PARAMNOTOPTIONAL|必須のパラメーターが省略されました。|  
  
## <a name="example"></a>例  
  
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
  
## <a name="see-also"></a>関連項目  
 [IDispatchEx インターフェイス](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)