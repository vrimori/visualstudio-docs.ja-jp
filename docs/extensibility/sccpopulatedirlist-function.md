---
title: SccPopulateDirList 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5315f3156f71310c92069ec3743232e98818b9a5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31137145"
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
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [特定のコマンドで使用されるビットフラグ](../extensibility/bitflags-used-by-specific-commands.md)   
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)   
 [エラー コード](../extensibility/error-codes.md)