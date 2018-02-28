---
title: "SccPopulateDirList 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 4be6e63df26d3c4a9b6539276aa97f69e349b83c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList 関数
この関数は、どのディレクトリおよび (必要に応じて) ファイルが、検査するディレクトリの一覧を指定して、ソース コントロールに格納されているを決定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SCCRTN SccPopulateDirList(  
   LPVOID        pContext,  
   LONG          nDirs,  
   LPCSTR*       lpDirPaths,  
   POPDIRLISTFUNCpfnPopulate,  
   LPVOID        pvCallerData,  
   LONG          fOptions  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pContext  
 [in]ソース管理プラグイン コンテキスト ポインターです。  
  
 nDirs  
 [in]内のディレクトリ パスの数、`lpDirPaths`配列。  
  
 lpDirPaths  
 [in]検査するディレクトリ パスの配列。  
  
 pfnPopulate  
 [in]各ディレクトリ パスと (必要に応じて) 内のファイル名に呼び出されるコールバック関数`lpDirPaths`(を参照してください[POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)詳細)。  
  
 pvCallerData  
 [in]コールバック関数に渡される値が変更されません。  
  
 foptions の   
 [in]ディレクトリの処理方法を制御する値の組み合わせ (の「PopulateDirList フラグ」セクションを参照して[ビットフラグが特定のコマンドで使用される](../extensibility/bitflags-used-by-specific-commands.md)使用可能な値)。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返す考えられます。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|操作が正常に完了しました。|  
|SCC_E_UNKNOWNERROR|エラーが発生しました。|  
  
## <a name="remarks"></a>コメント  
 ディレクトリとのみ (必要に応じて) ソース管理リポジトリに実際には、ファイル名は、コールバック関数に渡されます。  
  
## <a name="see-also"></a>参照  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [特定のコマンドで使用されるビットフラグ](../extensibility/bitflags-used-by-specific-commands.md)   
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)   
 [エラー コード](../extensibility/error-codes.md)