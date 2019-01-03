---
title: IDebugCodeContext2::GetLanguageInfo |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f6ed38b05e7e7453a5a3d622e0d5746964a41e6a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53889058"
---
# <a name="idebugcodecontext2getlanguageinfo"></a>IDebugCodeContext2::GetLanguageInfo
このコードのコンテキストの言語情報を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetLanguageInfo(   
   BSTR* pbstrLanguage,  
   GUID* pguidLanguage  
);  
```  
  
```csharp  
int GetLanguageInfo(   
   ref string pbstrLanguage,  
   ref Guid pguidLanguage  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pbstrLanguage`  
 [入力、出力]"C++"などの言語の名前を含む文字列を返します  
  
 `pguidLanguage`  
 [入力、出力]たとえば、コードのコンテキストの言語の GUID を返します`guidCPPLang`します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 Null 以外の値を返す、パラメーターの少なくとも 1 つ必要があります。  
  
## <a name="see-also"></a>関連項目  
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)