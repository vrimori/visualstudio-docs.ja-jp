---
title: "SccDirQueryInfo 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccDirQueryInfo
helpviewer_keywords: SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: aa1bc3624c8d03cfc484aaace906c2660c3a790e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="sccdirqueryinfo-function"></a>SccDirQueryInfo 関数
この関数は、現在の状態の完全修飾ディレクトリの一覧を調べます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SCCRTN SccDirQueryInfo(  
LPVOID  pContext,  
LONG    nDirs,  
LPCSTR* lpDirNames,  
LPLONG  lpStatus  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pContext  
 [in]ソース管理プラグイン コンテキスト構造体。  
  
 nDirs  
 [in]クエリを実行することを選択するディレクトリの数。  
  
 lpDirNames  
 [in]クエリを実行するディレクトリの完全修飾パスの配列。  
  
 lpStatus  
 [入力、出力].ソース管理の状態フラグを返すプラグインの配列構造体 (を参照してください[ディレクトリ ステータス コード](../extensibility/directory-status-code-enumerator.md)詳細)。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返す考えられます。  
  
|値|説明|  
|-----------|-----------------|  
|SCC_OK|クエリは成功しました。|  
|SCC_E_OPNOTSUPPORTED|ソース コード管理システムでは、この操作はサポートしません。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークや競合の問題の可能性があるためのアクセスに関する問題が発生しました。 再試行することをお勧めします。|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|不特定のエラーです。|  
  
## <a name="remarks"></a>コメント  
 関数は、入力からのビットのビットマスクの戻り値の配列、`SCC_DIRSTATUS`ファミリ (を参照してください[ディレクトリ ステータス コード](../extensibility/directory-status-code-enumerator.md))、指定されたディレクトリごとに 1 つのエントリ。 状態配列は、呼び出し元によって割り当てられます。  
  
 IDE は、対応するプロジェクトがあるかどうかを照会することで、ディレクトリがソース管理下にあるがかどうかをチェックするディレクトリの名前を変更する前に、この関数を使用します。 ディレクトリがソース管理下にない場合は、IDE は、ユーザーに適切な警告を提供できます。  
  
> [!NOTE]
>  ソース管理プラグイン状態の値の 1 つ以上を実装しない場合、実装されていないビットが 0 に設定する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [ディレクトリの状態コード](../extensibility/directory-status-code-enumerator.md)