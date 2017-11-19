---
title: "SccEnumChangedFiles 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccEnumChangedFiles
helpviewer_keywords: SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0ad62f14ea658e4af6e22d4beef410e6d9cf02df
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="sccenumchangedfiles-function"></a>SccEnumChangedFiles 関数
ローカル ファイルのリストを指定するには、この関数は、どのファイルとは異なるソース コード管理データベースに対応するバージョンを決定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SCCRTN SccEnumChangedFiles(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LONG    cFiles,  
   LPCSTR* lpFileNames,  
   LONG*   plIsFileDifferent  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pContext  
 [in]ソース管理プラグイン コンテキスト ポインターです。  
  
 hWnd  
 [in]ソース管理プラグインで提供されるダイアログ ボックスをすべての親として使用できる IDE ウィンドウへのハンドル。  
  
 cFiles  
 [in]指定されたファイル名の数、`lpFileNames`配列。 サイズを指定も`plIsFileDifferent`配列。  
  
 lpFileNames  
 [in]チェックするローカルのファイル名の配列です。  
  
 plIsFileDifferent  
 [入力、出力].各ファイルの相違点の状態を示す値の配列 (配列が少なくとも必要`cFiles`エントリ)。 0 以外では、ファイルが異なることを意味します。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返す考えられます。  
  
|値|説明|  
|-----------|-----------------|  
|SCC_OK|操作が正常に完了しました。|  
|SCC_UNSPECIFIEDERROR|一般エラーです。|  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)