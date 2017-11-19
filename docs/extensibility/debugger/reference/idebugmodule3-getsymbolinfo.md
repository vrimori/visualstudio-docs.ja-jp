---
title: "IDebugModule3::GetSymbolInfo |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugModule3::GetSymbolInfo
helpviewer_keywords:
- GetSymbolInfo method
- IDebugModule3::GetSymbolInfo method
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 341d31537f3c6c67e601296cf14eb5a6a10df08d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
各パスを検索の結果と、シンボル検索パスの一覧を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetSymbolInfo(  
   SYMBOL_SEARCH_INFO_FIELDS  dwFields,  
   MODULE_SYMBOL_SEARCH_INFO* pInfo  
);  
```  
  
```csharp  
int GetSymbolInfo(  
   enum_SYMBOL_SEARCH_INFO_FIELDS dwFields,   
   MODULE_SYMBOL_SEARCH_INFO[]    pinfo  
);  
  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwFields`  
 [in]フラグの組み合わせ、 [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)のどのフィールドを指定する列挙体`pInfo`を入力するのには、します。  
  
 `pInfo`  
 [out]A [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)構造体のメンバーは、指定した情報が入力されます。 このメソッドが戻るかどうかは、null 値と、`E_INVALIDARG`です。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功したかどうか、それを返します`S_OK`、それ以外のエラー コードを返します。  
  
> [!NOTE]
>  返される文字列 (で、`MODULE_SYMBOL_SEARCH_INFO`構造体) でしたを空にする場合でも`S_OK`が返されます。 この場合、返される検索情報がありませんでした。  
  
## <a name="remarks"></a>コメント  
 場合、`bstrVerboseSearchInfo`のフィールド、`MODULE_SYMBOL_SEARCH_INFO`構造が空ではありませんし、検索するパスと検索結果の一覧が含まれています。 一覧には、省略記号 ([...])、結果の後に続く、パスが表示されます。 1 つ以上のパスの結果のペアがある場合は、各ペアは、"\r\n"(-/改行) の組み合わせで区切られます。 パターンは、次のようになります。  
  
 \<パス >.\<結果 > \r\n\<パス >.\<結果 > \r\n\<パス >.\<結果 >  
  
 最後のエントリに \r\n のシーケンスがないことに注意してください。  
  
## <a name="example"></a>例  
 この例では、このメソッドは、次の 3 つの別の検索結果に 3 つのパスを返します。 各行は、キャリッジ リターンとライン フィードのペアで終了します。 だけ、出力の例は、1 つの文字列として、検索結果を印刷します。  
  
> [!NOTE]
>  状態の結果は、すべての行の末尾まで「...」の直後です。  
  
```cpp  
void ShowSymbolSearchResults(IDebugModule3 *pIDebugModule3)  
{  
    MODULE_SYMBOL_SEARCH_INFO ssi = { 0 };  
    HRESULT hr;  
    hr = pIDebugModule3->GetSymbolInfo(SSIF_VERBOSE_SEARCH_INFO,&ssi);  
    if (SUCCEEDED(hr)) {  
        CComBSTR searchInfo = ssi.bstrVerboseSearchInfo;  
        if (searchInfo.Length() != 0) {  
            std::wcout << (wchar_t *)(BSTR)searchInfo;  
            std::wcout << std::endl;  
        }  
    }  
}  
```  
  
 **c:\symbols\user32.pdb しています.ファイルが見つかりません。**  
**c:\winnt\symbols\user32.pdb しています.バージョンが一致しません。**  
**\\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb しています.シンボルが読み込まれます。**   
## <a name="see-also"></a>関連項目  
 [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)   
 [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)   
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)