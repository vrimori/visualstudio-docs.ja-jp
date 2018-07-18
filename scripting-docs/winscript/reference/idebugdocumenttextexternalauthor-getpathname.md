---
title: IDebugDocumentTextExternalAuthor::GetPathName |Microsoft ドキュメント
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
ms.openlocfilehash: 93e5c27422d6b348d8c961d1555bfce07183e9e4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727742"
---
# <a name="idebugdocumenttextexternalauthorgetpathname"></a>IDebugDocumentTextExternalAuthor::GetPathName
ドキュメントの完全パスとファイル名を返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pbstrLongName`  
 [out]完全パスとファイル名を含む文字列します。  
  
 `pfIsOriginalFile`  
 [out]かどうか、パスとファイル名の参照を示すブール値、元のドキュメントにします。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
|`E_FAIL`|ソース ファイルを作成または確認できません。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、ドキュメントの完全パスとファイル名を返します。  
  
 場合`pfIsOriginalFile`FALSE、パスとファイル名は、`pbstrLongName`新しく作成された一時ファイルを参照してください。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentTextExternalAuthor インターフェイス](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)