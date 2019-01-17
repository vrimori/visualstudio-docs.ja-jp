---
title: IDebugDocumentTextExternalAuthor::GetPathName |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextExternalAuthor.GetPathName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentTextExternalAuthor::GetPathName
ms.assetid: 445152a1-9cf8-402e-93d6-3d4bf2b81d17
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e17d27a320eac95445c083c718f5abcebbbc46cf
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088843"
---
# <a name="idebugdocumenttextexternalauthorgetpathname"></a>IDebugDocumentTextExternalAuthor::GetPathName
ドキュメントの完全なパスとファイル名を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pbstrLongName`  
 [out]完全なパスとファイル名を含む文字列します。  
  
 `pfIsOriginalFile`  
 [out]パスとファイル名が参照するかどうかを示すブール値、元のドキュメントにします。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
|`E_FAIL`|ソース ファイルを作成または決定できません。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、ドキュメントの完全なパスとファイル名を返します。  
  
 場合`pfIsOriginalFile`FALSE、パスとファイル名は、`pbstrLongName`新しく作成された一時ファイルを参照してください。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentTextExternalAuthor インターフェイス](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)