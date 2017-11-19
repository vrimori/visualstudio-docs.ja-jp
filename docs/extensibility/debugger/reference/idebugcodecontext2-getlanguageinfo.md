---
title: "IDebugCodeContext2::GetLanguageInfo |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords: IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b2b2f6f49b7ee8ebdf356a25bc2531aa2b8b9cf8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
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
 [入力、出力]."C++"など、言語の名前を表す文字列を返します  
  
 `pguidLanguage`  
 [入力、出力].たとえば、コードのコンテキストの言語の GUID を返します`guidCPPLang`です。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 Null 以外の値を返す、パラメーターの少なくとも 1 つ必要があります。  
  
## <a name="see-also"></a>関連項目  
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)