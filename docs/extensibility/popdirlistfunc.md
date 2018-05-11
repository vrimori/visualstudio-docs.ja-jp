---
title: POPDIRLISTFUNC |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 44a11e6edc9666fcd7614d467a2c9ffaa86b4365
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
これに指定されたコールバック関数、 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)ディレクトリおよび (必要に応じて) を検索するソース管理下にファイル名のコレクションを更新する関数。  
  
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
 [in]渡されたユーザー値[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)です。  
  
 bFolder  
 [in]`TRUE`場合内の名前`lpDirectoryOrFileName`ディレクトリです。 それ以外の場合、名前は、ファイル名。  
  
 lpDirectoryOrFileName  
 [in]ソース コード管理下にあるディレクトリまたはファイル名への完全なローカル パス。  
  
## <a name="return-value"></a>戻り値  
 IDE では、適切なエラー コードを返します。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|処理を続行します。|  
|SCC_I_OPERATIONCANCELED|処理を停止します。|  
|SCC_E_xxx|適切なソース制御エラーは、処理を停止する必要があります。|  
  
## <a name="remarks"></a>コメント  
 場合、`fOptions`のパラメーター、`SccPopulateDirList`関数が含まれて、`SCC_PDL_INCLUDEFILES`フラグでファイル名だけでなく、ディレクトリの名前は、一覧を含んでいる可能性がします。  
  
## <a name="see-also"></a>関連項目  
 [IDE によって実装されているコールバック関数](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)   
 [エラー コード](../extensibility/error-codes.md)