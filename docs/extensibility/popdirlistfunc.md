---
title: POPDIRLISTFUNC |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 37643aecf5e106c84121008423a391f8075c76fc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55005619"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
これに指定されたコールバック関数、 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)ディレクトリと (必要に応じて) ソース管理の対象であることを確認するファイル名のコレクションを更新する関数。  
  
 `POPDIRLISTFUNC`コールバックは、これらのディレクトリとファイル名に対してのみ呼び出す必要があります (に指定された一覧で、`SccPopulateDirList`関数)、ソース管理下に実際にします。  
  
## <a name="signature"></a>署名  
  
```cpp  
typedef BOOL (*POPDIRLISTFUNC)(  
   LPVOID pvCallerData,  
   BOOL bFolder,  
   LPCSTR lpDirectoryOrFileName  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 pvCallerData  
 [in]渡されたユーザー値[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)します。  
  
 bFolder  
 [in]`TRUE`場合に名前`lpDirectoryOrFileName`ディレクトリである名前のファイル名はそれ以外の場合。  
  
 lpDirectoryOrFileName  
 [in]ソース コード管理下にあるディレクトリまたはファイル名への完全なローカル パス。  
  
## <a name="return-value"></a>戻り値  
 IDE には、適切なエラー コードが返されます。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|処理を続行します。|  
|SCC_I_OPERATIONCANCELED|処理を停止します。|  
|SCC_E_xxx|適切なソース コントロール エラーは、処理を停止する必要があります。|  
  
## <a name="remarks"></a>Remarks  
 場合、`fOptions`のパラメーター、`SccPopulateDirList`関数が含まれています、`SCC_PDL_INCLUDEFILES`フラグでファイル名だけでなく、ディレクトリの名前は、一覧を含んでいる可能性が。  
  
## <a name="see-also"></a>関連項目  
 [IDE によって実装されるコールバック関数](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)   
 [エラー コード](../extensibility/error-codes.md)