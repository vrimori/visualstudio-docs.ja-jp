---
title: SccQueryInfo 関数 |Microsoft Docs
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
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a9b6de2b3c3894b6c6807995150707338e0d7162
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49183158"
---
# <a name="sccqueryinfo-function"></a>SccQueryInfo 関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

この関数は、一連のソース管理下で選択したファイルの状態情報を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 [入力、出力]配列をソース管理プラグインは各ファイルの状態フラグを返します。 詳細については、次を参照してください。[ファイルの状態コード](../extensibility/file-status-code-enumerator.md)します。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返すが必要です。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|クエリが正常に完了しました。|  
|SCC_E_ACCESSFAILURE|ソース管理システム、ネットワークまたは競合の問題である可能性のアクセスに問題が発生しました。 再試行をお勧めします。|  
|SCC_E_PROJNOTOPEN|プロジェクトでは、ソース管理下にある開いていません。|  
|SCC_E_NONSPECIFICERROR|不特定のエラーです。|  
  
## <a name="remarks"></a>Remarks  
 場合`lpFileName`は空の文字列を更新するステータス情報は現在ありません。 それ以外の場合、状態情報の変更を可能性がありますが、ファイルの完全なパス名になります。  
  
 戻り値の配列は、ビットマスクの`SCC_STATUS_xxxx`ビット。 詳細については、次を参照してください。[ファイルの状態コード](../extensibility/file-status-code-enumerator.md)します。 ソース管理システムはすべてのビットの種類をサポートしていません。 たとえば場合、`SCC_STATUS_OUTOFDATE`が提供されていない、ビットが設定されていないだけです。  
  
 ファイルをチェック アウトをこの関数を使用する場合は、次に注意してください`MSSCCI`状態の要件。  
  
-   `SCC_STATUS_OUTBYUSER` 現在のユーザーがチェック アウトするファイルと設定されます。  
  
-   `SCC_STATUS_CHECKEDOUT` 設定できません`SCC_STATUS_OUTBYUSER`設定されます。  
  
-   `SCC_STATUS_CHECKEDOUT` ときに、ファイルがチェック アウトを指定された作業ディレクトリにのみ設定されます。  
  
-   ファイルがチェック アウトされて現在のユーザーが、作業ディレクトリ以外のディレクトリに場合、`SCC_STATUS_OUTBYUSER`設定されているが、`SCC_STATUS_CHECKEDOUT`はありません。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [ファイルの状態コード](../extensibility/file-status-code-enumerator.md)

