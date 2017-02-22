---
title: "IDiaEnumTables | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaEnumTables インターフェイス"
ms.assetid: 016190c5-09e4-48f2-bf60-9b02603a03e0
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumTables
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

データ ソースに含まれるさまざまなテーブルを列挙します。  
  
## 構文  
  
```  
IDiaEnumTables : IUnknown  
```  
  
## Vtable の順序でメソッド  
 次の表は `IDiaEnumTables` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[IDiaEnumTables::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenumtables-get-newenum.md)|この列挙子の [IEnumVARIANT Interface](http://msdn.microsoft.com/ja-jp/139e3c93-faef-4003-9079-e0e94494db3e) のバージョンを取得します。|  
|[IDiaEnumTables::get\_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)|テーブルの数を取得します。|  
|[IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)|インデックスまたは名前でテーブルを取得します。|  
|[IDiaEnumTables::Next](../Topic/IDiaEnumTables::Next.md)|列挙体シーケンス内のテーブルの指定した数を取得します。|  
|[IDiaEnumTables::Skip](../../debugger/debug-interface-access/idiaenumtables-skip.md)|列挙体シーケンス内のテーブルの指定した数の要素をスキップします。|  
|[IDiaEnumTables::Reset](../Topic/IDiaEnumTables::Reset.md)|列挙体シーケンスを先頭にリセットします。|  
|[IDiaEnumTables::Clone](../../debugger/debug-interface-access/idiaenumtables-clone.md)|現在の列挙子と同じ列挙状態を含む列挙子を作成します。|  
  
## 解説  
  
## 呼び出し元のメモ  
 [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md) のメソッドを呼び出してこのインターフェイスを取得します。  
  
## 使用例  
 この例ではセッションで `IDiaEnumTables` のインターフェイスを取得する方法を示します。  テーブルを使用するコード例については[IDiaTable](../../debugger/debug-interface-access/idiatable.md) のインターフェイスを参照してください。  
  
```cpp#  
void ShowTableNames(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumTables> pTables;  
    if ( FAILED( psession->getEnumTables( &pTables ) ) )  
    {  
        Fatal( "getEnumTables" );  
    }  
    // Do something with table  
}  
```  
  
## 必要条件  
 ヘッダー : Dia2.h  
  
 ライブラリ : diaguids.lib  
  
 DLL: msdia80.dll  
  
## 参照  
 [インターフェイス \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)