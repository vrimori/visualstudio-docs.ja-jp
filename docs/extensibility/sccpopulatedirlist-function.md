---
title: SccPopulateDirList 関数 |Microsoft Docs
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
ms.openlocfilehash: 9b5839735e7564b486444cc0f9b65c71bc06f047
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847995"
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList 関数
この関数は、ディレクトリと (必要に応じて) ファイルがソース コントロールが確認するディレクトリの一覧に格納されているかを判断します。  
  
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
 [in]ソース管理プラグインのコンテキストのポインター。  
  
 nDirs  
 [in]内のディレクトリ パスの数、`lpDirPaths`配列。  
  
 lpDirPaths  
 [in]確認へのディレクトリ パスの配列。  
  
 pfnPopulate  
 [in]各ディレクトリのパスと (必要に応じて) ファイル名にするために呼び出すコールバック関数`lpDirPaths`(を参照してください[POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)詳細については)。  
  
 pvCallerData  
 [in]コールバック関数に渡される値は変更されません。  
  
 方法は限られて  
 [in]ディレクトリの処理方法を制御する値の組み合わせ (の「PopulateDirList フラグ」セクションを参照して[特定のコマンドで使用されるビットフラグ](../extensibility/bitflags-used-by-specific-commands.md)使用可能な値)。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返すが必要です。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|操作が正常に完了しました。|  
|SCC_E_UNKNOWNERROR|エラーが発生しました。|  
  
## <a name="remarks"></a>Remarks  
 これらのディレクトリとのみ (必要に応じて) 実際には、ソース管理リポジトリ内にあるファイル名は、コールバック関数に渡されます。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [特定のコマンドで使用されるビットフラグ](../extensibility/bitflags-used-by-specific-commands.md)   
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)   
 [エラー コード](../extensibility/error-codes.md)