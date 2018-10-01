---
title: IDebugDocumentContext2::GetLanguageInfo |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDocumentContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugDocumentContext2::GetLanguageInfo
ms.assetid: 6a212ee5-414c-4eb5-ab11-19db1786943d
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 53dc954fd36acc510ffe845188cd6075c5983f44
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537293"
---
# <a name="idebugdocumentcontext2getlanguageinfo"></a>IDebugDocumentContext2::GetLanguageInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugDocumentContext2::GetLanguageInfo](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo)します。  
  
このドキュメントのコンテキストに関連付けられた言語を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetLanguageInfo(   
   BSTR* pbstrLanguage,  
   GUID* pguidLanguage  
);  
```  
  
```csharp  
int GetLanguageInfo(   
   out string pbstrLanguage,  
   out Guid   pguidLanguage  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pbstrLanguage`  
 [out]このドキュメントのコンテキストでコードを実装する言語の名前を返します。  
  
 `pguidLanguage`  
 [out]このドキュメントのコンテキストでコードを実装する言語の GUID を返します。 たとえば、`guidVBScriptLang` または `guidCPPLang` のようにします。 この GUID は、によって指定された言語に制限がない[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="example"></a>例  
 次の例は、単純なは、このメソッドを実装する方法を示しています。`CDebugContext`を公開するオブジェクト、 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)インターフェイス。  
  
```cpp#  
HRESULT CDebugContext::GetLanguageInfo(BSTR* pbstrLanguage, GUID* pguidLanguage)    
{    
   HRESULT hr;    
  
   // Check for a valid language argument pointers.    
   if (pbstrLanguage && pguidLanguage)    
   {    
      *pguidLanguage = GUID_NULL;    
      *pbstrLanguage = SysAllocString(L"Batch File");    
      if (*pbstrLanguage)    
      {    
         *pguidLanguage = guidBatLang;    
         hr = S_OK;    
      }    
      else    
      {    
         hr = E_OUTOFMEMORY;    
      }    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}    
```  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)

