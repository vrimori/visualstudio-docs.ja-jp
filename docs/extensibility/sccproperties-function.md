---
title: "SccProperties 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccProperties"
helpviewer_keywords: 
  - "SccProperties 関数"
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# SccProperties 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この関数は、ファイルまたはプロジェクトのソース管理のプロパティを表示します。  
  
## 構文  
  
```cpp#  
SCCRTN SccProperties (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName  
);  
```  
  
#### パラメーター  
 pvContext  
 \[in\]ソース管理プラグイン コンテキスト構造体。  
  
 hwnd の分離  
 \[in\]ソース管理プラグインは、それによって提供されるダイアログ ボックスの親として使用できる IDE ウィンドウへのハンドル。  
  
 lpFileName  
 \[in\]ファイルまたはプロジェクトの完全修飾パス名。  
  
## 戻り値  
 この関数のソース コントロールのプラグインの実装は、次の値のいずれかを返す期待される結果します。  
  
|値|説明|  
|-------|--------|  
|SCC\_OK|プロパティが正常に表示されます。|  
|SCC\_I\_RELOADFILE|バージョン管理システムは変更して、ファイルのプロパティでは、IDE は、このファイルを再読み込みする必要があります。|  
|SCC\_E\_PROJNOTOPEN|ソース管理で、指定されたプロジェクトが開かれていません。|  
|SCC\_E\_NOTAUTHORIZED|ユーザーは、このファイルまたはプロジェクトのプロパティを表示する権限がありません。|  
|SCC\_E\_FILENOTCONTROLLED|指定したファイルまたはプロジェクトがソース管理下にあります。|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|未確認または一般的なエラーが発生しました。|  
  
## 解説  
 ソース管理プラグインでは、独自のダイアログ ボックスで、プロパティを表示します。  
  
 プロパティは、ソース管理プラグインで定義されており、プラグインをプラグインと異なる可能性があります。 返すように、プラグインできるように、ファイルのソース コントロールのプロパティを変更するユーザー、 `SCC_I_RELOAD` をこのファイルまたはプロジェクトの再読み込みする必要がある IDE を通知します。  
  
## 参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)