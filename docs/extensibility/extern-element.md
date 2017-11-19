---
title: "Extern 要素 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 764b6ff8b19711cb05f34c9bf652956057318346
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="extern-element"></a>Extern 要素
Extern 要素では、コンパイル時に、.vsct ファイルとマージする外部ヘッダー (.h) ファイルを参照します。 VSCT コンパイラに与えられたまたはによって参照されるインクルード パスにファイルをマージする必要があります、 [Include 要素](../extensibility/include-element.md)です。 ファイルには、他の .vsct ファイルまたは C++ ヘッダー ファイルがあります。  
  
 ヘッダー ファイルで定義する必要があります形式である"# [シンボル] [値] を define"値は、以前に定義されている場合、別のシンボル可能性があります。 コマンドの項目の条件付きステートメントでは、定義を使用することがあります。 実際に使用される任意の記号は破棄されます。  
  
 CommandTable 要素  
Extern 要素  
  
## <a name="syntax"></a>構文  
  
```  
<Extern href="stdidcmd.h" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|href|必須です。 ヘッダー ファイルへのパス:<br /><br /> href="stdidcmd.h"|  
|状態|省略可能です。 参照してください[条件付き属性](../extensibility/vsct-xml-schema-conditional-attributes.md)です。|  
|language|省略可能です。 すべての既定の言語[\<文字列 >](../extensibility/strings-element.md)コマンド テーブル内の要素。<br /><br /> language ="en-us"|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|なし。|なし。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[CommandTable 要素](../extensibility/commandtable-element.md)|すべてのコマンドを表す要素を定義します: メニュー項目、メニューのツールバー、およびコンボ ボックスは、-、IDE に VSPackage が提供します。|  
  
## <a name="example"></a>例  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-  
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>  
    ...  
  <Commands package="guidMyPackage">  
</CommandTable>  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio コマンド テーブル (です。Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Vspackage がユーザー インターフェイス要素を追加する方法](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [コマンド、メニュー、およびツール バー](../extensibility/internals/commands-menus-and-toolbars.md)