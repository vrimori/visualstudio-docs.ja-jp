---
title: SccPopulateDirList 関数 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4ebfe2e28eb020547c65afd603d1899ebde510a8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755920"
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList 関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

この関数は、ディレクトリと (必要に応じて) ファイルがソース コントロールが確認するディレクトリの一覧に格納されているかを判断します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SCCRTN SccPopulateDirList(  
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

