---
title: "QUERYCHANGESFUNC |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 43add362011b31ce695e9a8d9e77d6ca2dedb0e2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
これで使用されるコールバック関数、 [SccQueryChanges](../extensibility/sccquerychanges-function.md)操作がファイル名のコレクションを列挙し、各ファイルの状態を判断します。  
  
 `SccQueryChanges`関数ポインター、およびファイルの一覧を指定、`QUERYCHANGESFUNC`コールバック。 ソース管理プラグインは、指定された一覧を列挙し、一覧内の各ファイル (このコールバック) を使用して状態を提供します。  
  
## <a name="signature"></a>署名  
  
```cpp  
typedef BOOL (*QUERYCHANGESFUNC)(  
   LPVOID pvCallerData,  
   QUERYCHANGESDATA * pChangesData  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 pvCallerData  
 [in]`pvCallerData`に呼び出し元 (IDE) によって渡されたパラメーター [SccQueryChanges](../extensibility/sccquerychanges-function.md)です。 ソース管理プラグインには、この値の内容に関する想定を行いません。  
  
 pChangesData  
 [in]ポインター、 [QUERYCHANGESDATA 構造](#LinkQUERYCHANGESDATA)ファイルへの変更を記述する構造体。  
  
## <a name="return-value"></a>戻り値  
 IDE では、適切なエラー コードを返します。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|処理を続行します。|  
|SCC_I_OPERATIONCANCELED|処理を停止します。|  
|SCC_E_xxx|適切な SCC エラーは、処理を停止する必要があります。|  
  
##  <a name="LinkQUERYCHANGESDATA"></a>QUERYCHANGESDATA 構造体  
 各ファイルに渡された構造体は、次のようになります。  
  
```cpp  
struct QUERYCHANGESDATA_A  
{  
    DWORD  dwSize;  
    LPCSTR lpFileName;  
    DWORD  dwChangeType;  
    LPCSTR lpLatestName;  
};  
  
typedef struct QUERYCHANGESDATA_A QUERYCHANGESDATA;  
  
struct QUERYCHANGESDATA_W  
{  
    DWORD   dwSize;  
    LPCWSTR lpFileName;  
    DWORD   dwChangeType;  
    LPCWSTR lpLatestName;  
};  
```  
  
 dwSize  
 バイト単位でこの構造体のサイズ。  
  
 lpFileName  
 この項目の元のファイル名。  
  
 dwChangeType  
 ファイルの状態を示すコード。  
  
|コード|説明|  
|----------|-----------------|  
|`SCC_CHANGE_UNKNOWN`|変更内容を判断できません。|  
|`SCC_CHANGE_UNCHANGED`|このファイルの名前変更はありません。|  
|`SCC_CHANGE_DIFFERENT`|別の id を持つファイルが、同じ名前がデータベースに存在します。|  
|`SCC_CHANGE_NONEXISTENT`|ファイルは、データベース内、またはローカルに存在しません。|  
|`SCC_CHANGE_DATABASE_DELETED`|ファイルは、データベースで削除します。|  
|`SCC_CHANGE_LOCAL_DELETED`|ファイルがローカルで削除されましたが、ファイルは、データベースに引き続き存在します。 これを特定できない場合に返す`SCC_CHANGE_DATABASE_ADDED`です。|  
|`SCC_CHANGE_DATABASE_ADDED`|ファイルは、データベースに追加されたが、ローカルに存在しません。|  
|`SCC_CHANGE_LOCAL_ADDED`|ファイルはデータベースに存在しません、新しいローカル ファイルです。|  
|`SCC_CHANGE_RENAMED_TO`|ファイルの名前を変更またはとデータベースに移動`lpLatestName`です。|  
|`SCC_CHANGE_RENAMED_FROM`|ファイルの名前を変更または元のデータベース内で移動`lpLatestName`。 これは、追跡するために、価格が高すぎる場合など、別のフラグを返す`SCC_CHANGE_DATABASE_ADDED`です。|  
  
 lpLatestName  
 この項目の現在のファイル名。  
  
## <a name="see-also"></a>参照  
 [IDE によって実装されているコールバック関数](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)   
 [エラー コード](../extensibility/error-codes.md)