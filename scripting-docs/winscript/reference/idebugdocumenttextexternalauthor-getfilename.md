---
title: IDebugDocumentTextExternalAuthor::GetFileName |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextExternalAuthor.GetFileName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentTextExternalAuthor::GetFileName
ms.assetid: 87acdce6-acb2-4936-80dd-d624bb7dbd42
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9fc2532530044b7b3da286bce95152c704bf2392
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726612"
---
# <a name="idebugdocumenttextexternalauthorgetfilename"></a>IDebugDocumentTextExternalAuthor::GetFileName
パス情報がない場合、ドキュメントの名前を返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetFileName(  
   BSTR*  pbstrShortName  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pbstrShortName`  
 [out]ドキュメントの短い名前を含む文字列です。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、パス情報がない場合、ドキュメントの名前を返します。 通常、短い名前はダイアログ ボックスで使用されます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentTextExternalAuthor インターフェイス](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)