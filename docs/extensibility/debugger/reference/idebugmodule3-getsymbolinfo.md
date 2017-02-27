---
title: "IDebugModule3::GetSymbolInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModule3::GetSymbolInfo"
helpviewer_keywords: 
  - "GetSymbolInfo メソッド"
  - "IDebugModule3::GetSymbolInfo メソッド"
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# IDebugModule3::GetSymbolInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

各パスを検索の結果と、シンボル検索パスの一覧を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetSymbolInfo(  
   SYMBOL_SEARCH_INFO_FIELDS  dwFields,  
   MODULE_SYMBOL_SEARCH_INFO* pInfo  
);  
```  
  
```c#  
int GetSymbolInfo(  
   enum_SYMBOL_SEARCH_INFO_FIELDS dwFields,   
   MODULE_SYMBOL_SEARCH_INFO[]    pinfo  
);  
  
```  
  
#### パラメーター  
 `dwFields`  
 \[in\]フラグの組み合わせ、 [SYMBOL\_SEARCH\_INFO\_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) のどのフィールドを指定する列挙体 `pInfo` を入力するのには。  
  
 `pInfo`  
 \[out\]A [MODULE\_SYMBOL\_SEARCH\_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) 構造体のメンバーでは、指定した情報を使用して入力されます。 このメソッドが戻るかどうかは、null 値は、 `E_INVALIDARG`です。  
  
## 戻り値  
 メソッドが成功したかどうか、それを返します `S_OK`。 そうしないと、エラー コードを返します。  
  
> [!NOTE]
>  返される文字列 \(で、 `MODULE_SYMBOL_SEARCH_INFO` 構造\) 空にすることも `S_OK` が返されます。 この場合、返される情報を検索することはありません。  
  
## 解説  
 場合、 `bstrVerboseSearchInfo` のフィールド、 `MODULE_SYMBOL_SEARCH_INFO` 構造体は、空で、検索するパスと検索結果の一覧が含まれています。 一覧には、省略記号 \(「...」\)、結果の後に続く、パスが表示されます。 1 つ以上のパスの結果のペアがある場合は、各ペアは"\\r\\n"\(キャリッジ リターン\/改行\) の組み合わせによって区切られます。 パターンは、次のようになります。  
  
 \< パス \>... \< 結果 \> \\r\\n \< パス \>... \< 結果 \> \\r\\n \< パス \>... \< 結果 \>  
  
 最後のエントリに \\r\\n シーケンスがないことに注意してください。  
  
## 使用例  
 この例では、このメソッドは、次の 3 つの別の検索結果に 3 つのパスを返します。 各行はキャリッジ リターンとライン フィードのペアで終了します。 出力例では、単一の文字列で検索結果だけ印刷します。  
  
> [!NOTE]
>  状態の結果行の末尾まで「...」のすぐ後すべてがあります。  
  
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
  
 **c:\\symbols\\user32.pdb.ファイルが見つかりません。 c:\\winnt\\symbols\\user32.pdb.バージョンが一致しません。 \\\\symbols\\symbols\\user32.dll\\0a8sd0ad8ad\\user32.pdb.シンボルが読み込まれます。**   
## 参照  
 [SYMBOL\_SEARCH\_INFO\_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)   
 [MODULE\_SYMBOL\_SEARCH\_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)   
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)