---
title: "SccQueryInfo 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccQueryInfo
helpviewer_keywords: SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e5c2e974fe2cd0f6d95b97bba0ba2ffa22c1095e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="sccqueryinfo-function"></a>SccQueryInfo 関数
この関数は、一連のソース管理下で選択したファイルの状態に関する情報を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SCCRTN SccQueryInfo(  
   LPVOID  pvContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPLONG  lpStatus  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pvContext  
 [in]ソース管理プラグイン コンテキスト構造体。  
  
 nFiles  
 [in]指定されたファイルの数、`lpFileNames`配列との長さ、`lpStatus`配列。  
  
 lpFileNames  
 [in]クエリを実行するファイルの名前の配列。  
  
 lpStatus  
 [入力、出力].ソース管理プラグインが各ファイルのステータスのフラグを返すに配列です。 詳細については、次を参照してください。[ファイル ステータス コード](../extensibility/file-status-code-enumerator.md)です。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返す考えられます。  
  
|値|説明|  
|-----------|-----------------|  
|SCC_OK|クエリが正常に完了しました。|  
|SCC_E_ACCESSFAILURE|ソース管理システム、ネットワークや競合の問題の原因として可能性へのアクセスに問題が発生しました。 再試行することをお勧めします。|  
|SCC_E_PROJNOTOPEN|プロジェクトは、ソース管理下で開かれていません。|  
|SCC_E_NONSPECIFICERROR|不特定のエラーです。|  
  
## <a name="remarks"></a>コメント  
 場合`lpFileName`、空の文字列を更新するステータス情報は現在ありません。 それ以外の場合、ステータス情報の変更を可能性がありますが、ファイルの完全なパスの名前です。  
  
 戻り値の配列は、のビットマスク`SCC_STATUS_xxxx`ビットです。 詳細については、次を参照してください。[ファイル ステータス コード](../extensibility/file-status-code-enumerator.md)です。 ソース管理システムはすべてのビットの種類をサポートしていません。 たとえば場合、`SCC_STATUS_OUTOFDATE`は提供されません、ビットが設定されていないだけです。  
  
 この関数を使用して、ファイルをチェック アウトする、次を注意してください。`MSSCCI`状態の要件。  
  
-   `SCC_STATUS_OUTBYUSER`現在のユーザーがファイルをチェック アウト時に設定されています。  
  
-   `SCC_STATUS_CHECKEDOUT`以外は設定できません`SCC_STATUS_OUTBYUSER`が設定されています。  
  
-   `SCC_STATUS_CHECKEDOUT`ときに、ファイルはチェック アウトされた作業ディレクトリにのみ設定されます。  
  
-   ファイルがチェック アウトされて現在のユーザーが、作業ディレクトリ以外のディレクトリに場合、`SCC_STATUS_OUTBYUSER`設定されているが、`SCC_STATUS_CHECKEDOUT`はありません。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [ファイルの状態コード](../extensibility/file-status-code-enumerator.md)