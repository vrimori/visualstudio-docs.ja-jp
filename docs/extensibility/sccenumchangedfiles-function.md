---
title: SccEnumChangedFiles 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 762bda21f8480224347bd0c8c202c282298e07cc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|操作が正常に完了しました。|  
|SCC_UNSPECIFIEDERROR|一般エラーです。|  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)