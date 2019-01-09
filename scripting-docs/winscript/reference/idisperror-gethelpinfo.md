---
title: IDispError::GetHelpInfo |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetHelpInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetHelpInfo
ms.assetid: a146df13-eda4-4e56-8bf0-cf9886a2150f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c2c8ae3a3cff2485c50901bb94ced83098e6000
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087491"
---
# <a name="idisperrorgethelpinfo"></a>IDispError::GetHelpInfo
ヘルプ ファイルのパスと可能な場合、エラーを説明するトピックのコンテキスト ID を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetHelpInfo(  
   BSTR*  pbstrFileName,  
   DWORD*  pdwContext  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pbstrFileName`  
 [out]ヘルプ ファイルの完全修飾パスを表す文字列です。 ヘルプ ファイルがない、またはエラーが発生した、戻り値は NULL です。  
  
 `pdwContext`  
 [out]エラーのヘルプ コンテキスト ID。 ヘルプ ファイルが存在しない場合 (場合`pbstrFileName`null)、このパラメーターには意味がありません。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
|`E_FAIL`|プロバイダー固有のエラーが発生しました。|  
|`E_INVALIDARG`|`pbstrFileName` または`pdwContext`が NULL でした。|  
|`E_OUTOFMEMORY`|プロバイダーは、ヘルプ ファイルのパスを取得するための十分なメモリを割り当てることができませんでした。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、ヘルプ ファイルのパスと可能な場合、エラーを説明するトピックのコンテキスト ID を返します。  
  
> [!NOTE]
>  このメソッドは実装されていません。  
  
## <a name="see-also"></a>関連項目  
 [IDispError インターフェイス](../../winscript/reference/idisperror-interface.md)