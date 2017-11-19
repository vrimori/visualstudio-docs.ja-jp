---
title: "IDispError::GetHelpInfo |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDispError.GetHelpInfo
apilocation: scrobj.dll
helpviewer_keywords: IDispError::GetHelpInfo
ms.assetid: a146df13-eda4-4e56-8bf0-cf9886a2150f
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17098b4055bb61e9a2f639404edfe2214abc931e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idisperrorgethelpinfo"></a>IDispError::GetHelpInfo
ヘルプ ファイルのパスと可能な場合、エラーを説明するトピックのコンテキスト ID を返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetHelpInfo(  
   BSTR*  pbstrFileName,  
   DWORD*  pdwContext  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pbstrFileName`  
 [out]ヘルプ ファイルの完全修飾パスを含む文字列です。 ヘルプ ファイルがない、またはエラーが発生した、戻り値は NULL です。  
  
 `pdwContext`  
 [out]エラーのヘルプ コンテキスト ID です。 ヘルプ ファイルがない場合 (場合`pbstrFileName`null)、このパラメーターは意味を持ちません。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
|`E_FAIL`|プロバイダー固有のエラーが発生しました。|  
|`E_INVALIDARG`|`pbstrFileName`または`pdwContext`が NULL です。|  
|`E_OUTOFMEMORY`|プロバイダーは、ヘルプ ファイルのパスを取得するための十分なメモリを割り当てることができませんでした。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、ヘルプ ファイルのパスと可能な場合、エラーを説明するトピックのコンテキスト ID を返します。  
  
> [!NOTE]
>  このメソッドは実装されていません。  
  
## <a name="see-also"></a>関連項目  
 [IDispError インターフェイス](../../winscript/reference/idisperror-interface.md)