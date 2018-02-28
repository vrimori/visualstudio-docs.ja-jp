---
title: "IDebugStackFrame2::GetLanguageInfo |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugStackFrame2::GetLanguageInfo
helpviewer_keywords:
- IDebugStackFrame2::GetLanguageInfo
ms.assetid: 0e12fd92-f155-46a7-8272-cda279388cfb
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 12e27e744d13ce24f90a4c97ea242cecf8a843d5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugstackframe2getlanguageinfo"></a>IDebugStackFrame2::GetLanguageInfo
このスタック フレームに関連する言語を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
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
 [out]返します、`GUID`言語です。 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]言語、たとえば、次返すことのできます。  
  
-   `guidVBScriptLang`  
  
-   `guidJScriptLang`  
  
-   `guidCPPLang`  
  
-   `guidVBLang`  
  
-   `guidSQLLang`  
  
-   `guidScriptLang`  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>参照  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)