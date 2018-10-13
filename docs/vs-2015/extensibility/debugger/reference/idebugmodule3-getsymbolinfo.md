---
title: IDebugModule3::GetSymbolInfo |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugModule3::GetSymbolInfo
helpviewer_keywords:
- GetSymbolInfo method
- IDebugModule3::GetSymbolInfo method
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cb153568c21af8c7b870583adb8b3189c7e3c8cd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49294022"
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

各パスの検索の結果と同様にシンボルを検索するパスの一覧を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 [in]フラグの組み合わせ、 [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)のどのフィールドを指定する列挙体`pInfo`入力します。  
  
 `pInfo`  
 [out]A [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)構造体のメンバーは、指定した情報が入力されます。 このメソッドが戻るかどうかは、null 値と、`E_INVALIDARG`します。  
  
## <a name="return-value"></a>戻り値  
 返します、メソッドが成功したかどうかは`S_OK`、それ以外のエラー コードを返します。  
  
> [!NOTE]
>  返される文字列 (で、`MODULE_SYMBOL_SEARCH_INFO`構造) 空にすることも`S_OK`が返されます。 この場合、返される検索情報がありませんでした。  
  
## <a name="remarks"></a>Remarks  
 場合、`bstrVerboseSearchInfo`のフィールド、`MODULE_SYMBOL_SEARCH_INFO`構造体が空ではありませんし、検索するパスと検索結果の一覧が含まれています。 一覧には、省略記号 (「...」)、結果の後に続く、パスが表示されます。 1 つ以上のパスの結果のペアがある場合は、各ペアは"\r\n"(復帰と改行) のペアによって区切られます。 パターンのようになります。  
  
 \<パス >.\<結果 > \r\n\<パス >.\<結果 > \r\n\<パス >.\<結果 >  
  
 最後のエントリに \r\n シーケンスがないことに注意してください。  
  
## <a name="example"></a>例  
 この例では、このメソッドは、3 つの別の検索結果に 3 つのパスを返します。 各行は復帰と改行のペアで終了します。 出力の例では、1 つの文字列として、検索結果だけ印刷します。  
  
> [!NOTE]
>  状態の結果は、行の末尾まで「...」の直後に続くれます。  
  
```cpp#  
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
  
 **c:\symbols\user32.pdb.ファイルが見つかりませんでした。**  
**c:\winnt\symbols\user32.pdb.バージョンが一致しません。**  
**\\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb.シンボルが読み込まれます。**   
## <a name="see-also"></a>関連項目  
 [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)   
 [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)   
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)

