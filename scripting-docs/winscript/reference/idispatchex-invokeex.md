---
title: IDispatchEx::InvokeEx |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.InvokeEx
apilocation:
- scrobj.dll
helpviewer_keywords:
- InvokeEx method
ms.assetid: d90783e6-4b89-4423-8a56-a9c8b4b2c813
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e631ecca1181a25fa3cf419f5fc96666f0db3cd6
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086529"
---
# <a name="idispatchexinvokeex"></a>IDispatchEx::InvokeEx
プロパティとによって公開されるメソッドにアクセスできるように、`IDispatchEx`オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```cpp
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
 有効な値`wFlags`は。  
  
 DISPATCH_PROPERTYGET &AMP;#124; DISPATCH_METHOD &AMP;#124; DISPATCH_PROPERTYPUT &AMP;#124; DISPATCH_PROPERTYPUTREF &AMP;#124; DISPATCH_CONSTRUCT  
  
 コンテキストを記述するフラグ、`InvokeEx`呼び出し。  
  
|[値]|説明|  
|-----------|-------------|  
|DISPATCH_METHOD|メンバーがメソッドとして呼び出されます。 プロパティに同じ名前がある場合は、これと DISPATCH_PROPERTYGET フラグの両方を設定することがあります (によって定義された`IDispatch`)。|  
|DISPATCH_PROPERTYGET|メンバーがプロパティまたはデータ メンバーとして取得される (によって定義された`IDispatch`)。|  
|DISPATCH_PROPERTYPUT|メンバーが変更されたプロパティまたはデータ メンバー (によって定義された`IDispatch`)。|  
|DISPATCH_PROPERTYPUTREF|値の割り当てではなく、参照の割り当てによってメンバーが変更されます。 このフラグは、プロパティがオブジェクトへの参照を受け入れる場合にのみ有効です (によって定義された`IDispatch`)。|  
|DISPATCH_CONSTRUCT|メンバーは、コンス トラクターとして使用されています。 (これは、新しい値によって定義された`IDispatchEx`)。 有効な値`wFlags`は。<br /><br /> DISPATCH_PROPERTYGET DISPATCH_METHOD DISPATCH_PROPERTYPUT DISPATCH_PROPERTYPUTREF DISPATCH_CONSTRUCT|  
  
 `pdp`  
 引数の配列、名前付き引数の DISPID の配列、配列内の要素数のカウントを格納している構造体へのポインター。 参照してください、 `IDispatch` DISPPARAMS 構造体の詳細についてはドキュメントです。  
  
 `pVarRes`  
 結果が保存または呼び出し元が結果を持たない場合は Null にする場所へのポインター。 この引数には、DISPATCH_PROPERTYPUT または DISPATCH_PROPERTYPUTREF を指定した場合は無視されます。  
  
 `pei`  
 例外情報を格納する構造体へのポインター。 この構造体の場合に塗りつぶしが必要`DISP_E_EXCEPTION`が返されます。 Null にすることができます。 参照してください、`IDispatch`ドキュメントの詳細については、`EXCEPINFO`構造体。  
  
 `pspCaller`  
 呼び出し元からサービスを取得するオブジェクトは、呼び出し元によって提供されるサービス プロバイダー オブジェクトへのポインター。 Null にすることができます。  
  
 `IDispatchEx::InvokeEx` すべてのと同じ機能を提供`IDispatch::Invoke`一部の拡張機能を追加します。  
  
|||  
|-|-|  
|DISPATCH_CONSTRUCT|項目が、コンス トラクターとして使用されていることを示します。|  
|`pspCaller`|`pspCaller`呼び出し元が提供するサービス オブジェクトへのアクセス許可。 特定のサービスは、呼び出し側自体によって処理または呼び出しチェーンの上位にさらに呼び出し元に委任可能性があります。 たとえば、内のスクリプト エンジンの場合、ブラウザーが、`InvokeEx`外部オブジェクト、オブジェクトへの呼び出しをフォローできます、`pspCaller`チェーン スクリプト エンジンまたはブラウザーからサービスを取得します。 (呼び出しチェーンではありません作成チェーンと同じ-コンテナーのチェーンやチェーンのサイトとも呼ばれます。 作成チェーンできるよう他のメカニズムによってなど`IObjectWithSite`)。|  
|`this` ポインター|DISPATCH_METHOD を設定すると`wFlags`、"this"値「名前付きパラメーター」である可能性があります。 DISPID は DISPID_THIS であり、最初の名前付きパラメーターがあります。|  
  
 未使用`riid`パラメーター`IDispatch::Invoke`が削除されました。  
  
 `puArgArr`パラメーター`IDispatch::Invoke`が削除されました。  
  
 参照してください、`IDispatch::Invoke`例については、次のドキュメント。  
  
 「引数なしでメソッドの呼び出し」  
  
 "を取得して、プロパティの設定"  
  
 「パラメーターの引き渡し」  
  
 [インデックスのプロパティ]  
  
 「呼び出し中に例外を発生させる」  
  
 「エラーを返す」  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|DISP_E_BADPARAMCOUNT|DISPPARAMS に提供される要素の数は、メソッドまたはプロパティが受け入れる引数の数によって異なります。|  
|DISP_E_BADVARTYPE|1 つの引数の`rgvarg`有効な variant 型ではありません。|  
|DISP_E_EXCEPTION|アプリケーションは、例外を発生させる必要があります。 渡された構造体の例では、`pei`に入力する必要があります。|  
|DISP_E_MEMBERNOTFOUND|要求されたメンバーが存在しないへの呼び出しまたは`InvokeEx`読み取り専用プロパティの値を設定しようとしました。|  
|DISP_E_NONAMEDARGS|この実装の`IDispatch`は名前付き引数をサポートしていません。|  
|DISP_E_OVERFLOW|1 つの引数の`rgvarg`指定した型に強制変換できませんでした。|  
|DISP_E_PARAMNOTFOUND|Dispid パラメーターの 1 つは、メソッドのパラメーターに対応していません。|  
|DISP_E_TYPEMISMATCH|1 つ以上の引数は、強制されませんでした。|  
|DISP_E_UNKNOWNLCID|呼び出されるメンバーは、LCID に従って文字列引数を解釈し、LCID が認識されていません。 LCID は、引数を解釈する必要はありません、このエラーが返されないようにします。|  
|DISP_E_PARAMNOTOPTIONAL|必要なパラメーターが省略されました。|  
  
## <a name="example"></a>例  
  
```cpp
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