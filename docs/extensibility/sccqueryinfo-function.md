---
title: "SccQueryInfo 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: a178aada6303ed21f51a6be66ba02b2145dcd694
ms.lasthandoff: 02/22/2017

---
# <a name="sccqueryinfo-function"></a>SccQueryInfo 関数
この関数は、一連のソース管理下で選択したファイルの状態に関する情報を取得します。  
  
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
 [in]指定されたファイルの数、`lpFileNames`配列の長さ、および、`lpStatus`配列。  
  
 lpFileNames  
 [in]クエリを実行するファイルの名前の配列。  
  
 lpStatus  
 [入力、出力]ソース管理プラグインが各ファイルのステータスのフラグを返す配列。 詳細については、次を参照してください。[ファイルのステータス コードは](../extensibility/file-status-code-enumerator.md)です。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース コントロールのプラグインの実装は、次の値のいずれかを返す期待される結果します。  
  
|値|説明|  
|-----------|-----------------|  
|SCC_OK|クエリが正常に完了しました。|  
|SCC_E_ACCESSFAILURE|おそらくネットワークや競合の問題の原因となったソース管理システムのアクセスに問題が発生しました。 再試行することをお勧めします。|  
|SCC_E_PROJNOTOPEN|プロジェクトは、ソース管理下で開かれていません。|  
|SCC_E_NONSPECIFICERROR|不特定のエラーです。|  
  
## <a name="remarks"></a>コメント  
 場合`lpFileName`空の文字列を更新するステータス情報は現在ありません。 それ以外の場合、ステータス情報の変更を可能性がありますが、ファイルの完全なパス名になります。  
  
 戻り値の配列は、のビットマスク`SCC_STATUS_xxxx`ビットです。 詳細については、次を参照してください。[ファイルのステータス コードは](../extensibility/file-status-code-enumerator.md)です。 ソース管理システムはすべての bit 型をサポートしていません。 たとえば場合、`SCC_STATUS_OUTOFDATE`が提供されない、ビットが設定されていないだけです。  
  
 この関数を使用して、ファイルをチェック アウトする、次を注意してください。`MSSCCI`ステータスの要件。  
  
-   `SCC_STATUS_OUTBYUSER`現在のユーザーがファイルをチェック アウト時に設定されています。  
  
-   `SCC_STATUS_CHECKEDOUT`以外は設定できません`SCC_STATUS_OUTBYUSER`が設定されます。  
  
-   `SCC_STATUS_CHECKEDOUT`ときに、ファイルがチェック アウト、指定された作業ディレクトリにのみ設定されます。  
  
-   場合は、ファイルがチェック アウトされて現在のユーザーが作業ディレクトリ以外のディレクトリに`SCC_STATUS_OUTBYUSER`設定されているが、`SCC_STATUS_CHECKEDOUT`はありません。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [ファイルの状態コード](../extensibility/file-status-code-enumerator.md)
