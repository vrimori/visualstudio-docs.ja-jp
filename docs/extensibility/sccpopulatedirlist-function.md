---
title: "SccPopulateDirList 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccPopulateDirList"
helpviewer_keywords: 
  - "SccPopulateDirList 関数"
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# SccPopulateDirList 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

フォルダーおよび \(必要に応じて\) ファイルが調べるディレクトリの一覧を指定したソース管理に格納されているかを判別します。  
  
## 構文  
  
```cpp  
SCCRTN SccPopulateDirList(  
   LPVOID        pContext,  
   LONG          nDirs,  
   LPCSTR*       lpDirPaths,  
   POPDIRLISTFUNCpfnPopulate,  
   LPVOID        pvCallerData,  
   LONG          fOptions  
);  
```  
  
#### パラメーター  
 pContext  
 \[in\]ソース管理プラグインのコンテキストのポインター。  
  
 nDirs  
 \[in\]内のディレクトリ パスの数、 `lpDirPaths` 配列。  
  
 lpDirPaths  
 \[in\]確認へのディレクトリ パスの配列。  
  
 pfnPopulate  
 \[in\]各ディレクトリのパスおよび \(オプション内のファイル名\) に呼び出されるコールバック関数 `lpDirPaths` \(を参照してください [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) 詳細\)。  
  
 pvCallerData  
 \[in\]コールバック関数に渡される値は変更されません。  
  
 される  
 \[in\]ディレクトリの処理方法を制御する値の組み合わせ \(の"PopulateDirList flags"を参照してください [特定のコマンドで使用されるビットフラグ](../extensibility/bitflags-used-by-specific-commands.md) 指定できる値について\)。  
  
## 戻り値  
 この関数のソース コントロールのプラグインの実装は、次の値のいずれかを返す期待される結果します。  
  
|値|説明|  
|-------|--------|  
|SCC\_OK|操作が完了しました。|  
|SCC\_E\_UNKNOWNERROR|エラーが発生しました。|  
  
## 解説  
 ディレクトリとのみ \(オプション\)、実際にはソース管理リポジトリにファイル名は、コールバック関数に渡されます。  
  
## 参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [特定のコマンドで使用されるビットフラグ](../extensibility/bitflags-used-by-specific-commands.md)   
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)   
 [エラー コード](../extensibility/error-codes.md)