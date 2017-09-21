---
title: "QUERYCHANGESFUNC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "QUERYCHANGESFUNC"
helpviewer_keywords: 
  - "QUERYCHANGESFUNC コールバック関数"
  - "QUERYCHANGESDATA 構造体"
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# QUERYCHANGESFUNC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

これで使用するコールバック関数、 [SccQueryChanges](../extensibility/sccquerychanges-function.md) ファイル名のコレクションを列挙し、各ファイルの状態を確認する操作。  
  
 `SccQueryChanges` 関数がファイルおよびへのポインターのリストを指定した、 `QUERYCHANGESFUNC` コールバックします。 ソース管理プラグインでは、指定したリストを列挙し、一覧内の各ファイル \(このコールバック\) を使用して状態を提供します。  
  
## Signature  
  
```cpp#  
typedef BOOL (*QUERYCHANGESFUNC)( LPVOID pvCallerData, QUERYCHANGESDATA * pChangesData );  
```  
  
## パラメーター  
 pvCallerData  
 \[in\] `pvCallerData` に呼び出し元 \(IDE\) で渡されるパラメーター [SccQueryChanges](../extensibility/sccquerychanges-function.md)します。 ソース管理プラグインには、この値の内容を判断する必要があります行いません。  
  
 pChangesData  
 \[in\]ポインター、 [QUERYCHANGESDATA 構造体](#LinkQUERYCHANGESDATA) ファイルに対する変更を記述する構造体。  
  
## 戻り値  
 IDE には、該当するエラー コードが返されます。  
  
|値|説明|  
|-------|--------|  
|SCC\_OK|処理を続行します。|  
|SCC\_I\_OPERATIONCANCELED|処理を停止します。|  
|SCC\_E\_xxx|適切な SCC エラーは、処理を停止する必要があります。|  
  
##  <a name="LinkQUERYCHANGESDATA"></a> QUERYCHANGESDATA 構造体  
 ファイルごとに渡された構造体は、次のようになります。  
  
```cpp#  
struct QUERYCHANGESDATA_A { DWORD  dwSize; LPCSTR lpFileName; DWORD  dwChangeType; LPCSTR lpLatestName; }; typedef struct QUERYCHANGESDATA_A QUERYCHANGESDATA; struct QUERYCHANGESDATA_W { DWORD   dwSize; LPCWSTR lpFileName; DWORD   dwChangeType; LPCWSTR lpLatestName; };  
```  
  
 dwSize  
 この構造体のサイズ \(単位: バイト\)。  
  
 lpFileName  
 このアイテムの元のファイル名。  
  
 dwChangeType  
 ファイルの状態を示すコード。  
  
|コード|説明|  
|---------|--------|  
|`SCC_CHANGE_UNKNOWN`|変更内容を判断できません。|  
|`SCC_CHANGE_UNCHANGED`|このファイルの名前が変更されていません。|  
|`SCC_CHANGE_DIFFERENT`|別の id を持つファイルが同じ名前がデータベースに存在します。|  
|`SCC_CHANGE_NONEXISTENT`|ファイルは、データベース内、またはローカルに存在しません。|  
|`SCC_CHANGE_DATABASE_DELETED`|ファイルは、データベースで削除します。|  
|`SCC_CHANGE_LOCAL_DELETED`|ファイルがローカルで削除されましたが、ファイルは、まだデータベースに存在します。 これを特定できない場合は、返す `SCC_CHANGE_DATABASE_ADDED`します。|  
|`SCC_CHANGE_DATABASE_ADDED`|ファイルはデータベースに追加しますが、ローカルに存在しません。|  
|`SCC_CHANGE_LOCAL_ADDED`|ファイルはデータベースに存在しません、新しいローカル ファイルです。|  
|`SCC_CHANGE_RENAMED_TO`|ファイルの名前を変更したりとしてデータベースに移動 `lpLatestName`します。|  
|`SCC_CHANGE_RENAMED_FROM`|ファイルの名前を変更したり移動元データベースで `lpLatestName`。 これは、追跡するために高価すぎる場合など、さまざまなフラグを返す `SCC_CHANGE_DATABASE_ADDED`します。|  
  
 lpLatestName  
 この項目の現在のファイル名。  
  
## 参照  
 [IDE で実装されるコールバック関数](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)   
 [エラー コード](../extensibility/error-codes.md)