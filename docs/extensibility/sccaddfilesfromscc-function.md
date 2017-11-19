---
title: "SccAddFilesFromSCC 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccAddFilesFromSCC
helpviewer_keywords: SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1764bfc503e25860326b1910c432edcf95c8f21c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="sccaddfilesfromscc-function"></a>SccAddFilesFromSCC 関数
この関数は、ソース管理からファイルの一覧を現在開いているプロジェクトに追加します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SCCRTN SccAddFilesFromSCC(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LPSTR   lpUser,  
   LPSTR   lpAuxProjPath,  
   LONG    cFiles,  
   LPCSTR* lpFilePaths,  
   LPCSTR  lpDestination,  
   LPCSTR  lpComment,  
   LPBOOL  pbResults  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pContext  
 [in]ソース管理プラグイン コンテキスト ポインターです。  
  
 hWnd  
 [in]ソース管理プラグインで提供されるダイアログ ボックスをすべての親として使用できる IDE ウィンドウへのハンドル。  
  
 lpUser  
 [入力、出力].(最大 SCC_USER_SIZE、null 終端文字を含む) のユーザー名。  
  
 lpAuxProjPath  
 [入力、出力].プロジェクトを識別する補助の文字列 (最大`SCC_PRJPATH_`サイズは、null 終端文字を含めて)。  
  
 cFiles  
 [in]によって指定されたファイルの数`lpFilePaths`です。  
  
 lpFilePaths  
 [入力、出力].現在のプロジェクトに追加するファイル名の配列です。  
  
 lpDestination  
 [in]ファイルが書き込まれる先のパス。  
  
 lpComment  
 [in]各追加されるファイルに適用されるコメントです。  
  
 pbResults  
 [入力、出力].エラーまたは 0 以外 (TRUE) に成功した場合に設定できるフラグの配列 (0 または FALSE) の各ファイルの (配列のサイズは以上である必要があります`cFiles`長い)。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返す考えられます。  
  
|値|説明|  
|-----------|-----------------|  
|SCC_E_PROJNOTOPEN|プロジェクトが開かれていません。|  
|SCC_E_OPNOTPERFORMED|接続では、同じプロジェクトで指定したとおりにありません。`lpAuxProjPath.`|  
|SCC_E_NOTAUTHORIZED|ユーザーは、データベースを更新する権限がありません。|  
|SCC_E_NONSPECIFICERROR|不明なエラーがあります。|  
|SCC_I_RELOADFILE|ファイルまたはプロジェクトは、再読み込みする必要があります。|  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)