---
title: "IActiveScriptAuthor::GetLanguageFlags | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetLanguageFlags
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetLanguageFlags"
ms.assetid: eb244452-62f7-4a73-b48f-1aa05cbcc32d
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# IActiveScriptAuthor::GetLanguageFlags
言語の情報を返します。  
  
## 構文  
  
```  
HRESULT GetLanguageFlags(  
   DWORD              *pgrfasa  
);  
```  
  
#### パラメーター  
 `pgrfasa`  
 \[出力\]言語の情報を示すフラグ。  次の値の組み合わせがあります:  
  
|定数|値|説明|  
|--------|-------|--------|  
|fasaPreferInternalHandler|0x0001|言語はアプリケーションではなく、スクリプト エンジンを作成してスクリプトのイベント ハンドラーを作成します。|  
|fasaSupportInternalHandler|0x0002|言語のサポートは、スクリプト エンジンを作成して作成されたイベント ハンドラーのスクリプトの作成。|  
|fasaCaseSensitive|0x0004|スクリプト言語が大文字と小文字が区別されます。|  
  
## 戻り値  
 `HRESULT`。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 エンジンの作成スクリプトのイベント ハンドラーを管理する場合、アプリケーションでは `IScriptEntry` のオブジェクトの `CreateChildHandler` を呼び出す必要があります。  これは、イベント ハンドラーに対応する `IScriptScriptlet` のオブジェクトを作成します。  エンジンは、スクリプトのエントリにイベント ハンドラーを追加します。  イベント ハンドラーは、指定したシグネチャ情報を含んだ空の関数です。  
  
 アプリケーションでイベント ハンドラーを管理する場合、イベント ハンドラーのスクリプトレットを表す `IScriptNode` のオブジェクトの `CreateChildHandler` を呼び出す必要があります。  これは、イベント ハンドラーのスクリプトレットに関連付けられている `IScriptScriptlet` のオブジェクトを作成します。  アプリケーションは、`IScriptEntry` 新規または既存のオブジェクトにイベント ハンドラーとして空の関数を追加する必要があります。  
  
## 参照  
 [IActiveScriptAuthor インターフェイス](../../winscript/reference/iactivescriptauthor-interface.md)