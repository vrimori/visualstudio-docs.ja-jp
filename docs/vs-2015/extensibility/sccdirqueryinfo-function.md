---
title: SccDirQueryInfo 関数 |Microsoft Docs
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
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f2df4dd52ff9984059eb28f21edf49b9db741358
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51784898"
---
# <a name="sccdirqueryinfo-function"></a>SccDirQueryInfo 関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

この関数は、その現在の状態の完全修飾ディレクトリの一覧を検証します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 [in]クエリを実行する選択されているディレクトリの数。  
  
 lpDirNames  
 [in]クエリを実行するディレクトリの完全修飾パスの配列。  
  
 lpStatus  
 [入力、出力]ソース管理の状態フラグを返すプラグインの配列構造体 (を参照してください[ディレクトリの状態コード](../extensibility/directory-status-code-enumerator.md)詳細については)。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返すが必要です。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|クエリが正常に完了しました。|  
|SCC_E_OPNOTSUPPORTED|ソース コード管理システムでは、この操作はサポートしません。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークまたは競合の問題の可能性へのアクセスに問題が発生しました。 再試行をお勧めします。|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|不特定のエラーです。|  
  
## <a name="remarks"></a>Remarks  
 関数からのビットのビットマスクを指定の戻り値の配列を格納する、`SCC_DIRSTATUS`ファミリ (を参照してください[ディレクトリの状態コード](../extensibility/directory-status-code-enumerator.md))、指定されたディレクトリごとに 1 つのエントリ。 状態配列は、呼び出し元によって割り当てられます。  
  
 IDE は、対応するプロジェクトがあるかどうかクエリを実行して、ディレクトリは、ソース管理下にあるかどうかをチェックするディレクトリの名前を変更する前に、この関数を使用します。 ソース管理下にあるディレクトリでない場合、IDE は、ユーザーに適切な警告を提供できます。  
  
> [!NOTE]
>  ソース管理プラグインのステータス値の 1 つ以上を実装しない場合、実装されていないビットを 0 に設定する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [ディレクトリの状態コード](../extensibility/directory-status-code-enumerator.md)

