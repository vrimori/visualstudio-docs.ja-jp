---
title: IDebugStackFrame2::GetLanguageInfo |Microsoft Docs
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
- IDebugStackFrame2::GetLanguageInfo
helpviewer_keywords:
- IDebugStackFrame2::GetLanguageInfo
ms.assetid: 0e12fd92-f155-46a7-8272-cda279388cfb
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0f588da1ae11939a8d05640dacb52bc62af87011
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47534760"
---
# <a name="idebugstackframe2getlanguageinfo"></a>IDebugStackFrame2::GetLanguageInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugStackFrame2::GetLanguageInfo](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugstackframe2-getlanguageinfo)します。  
  
このスタック フレームに関連付けられている言語を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetLanguageInfo (   
   BSTR* pbstrLanguage,  
   GUID* pguidLanguage  
);  
```  
  
```csharp  
int GetLanguageInfo (   
   ref string pbstrLanguage,  
   ref Guid   pguidLanguage  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pbstrLanguage`  
 [out]このスタック フレームに関連付けられているメソッドを実装する言語の名前を返します。  
  
 `pguidLanguage`  
 [out]返します、`GUID`の言語。 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]言語、たとえば、次を返せること。  
  
-   `guidVBScriptLang`  
  
-   `guidJScriptLang`  
  
-   `guidCPPLang`  
  
-   `guidVBLang`  
  
-   `guidSQLLang`  
  
-   `guidScriptLang`  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)

