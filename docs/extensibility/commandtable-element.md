---
title: "CommandTable 要素 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 6fe68f25748df171ec6695554903b37854e7d8c6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="commandtable-element"></a>CommandTable 要素
CommandTable は、.vsct ファイルのルート要素です。 これは、実際のレイアウトと、IDE に VSPackage が提供するコマンドの種類を定義するファイルです。 コマンドには、メニュー項目、メニューのツールバー、コンボ ボックスなどがあります。 詳細については、「 [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema" >  
  <Extern>... </Extern>  
  <Include>... </Include>  
  <Define>... </Define>  
  <Commands>... </Commands>  
  <CommandPlacements>... </CommandPlacements>  
  <VisibilityConstraints>... </VisibilityConstraints>  
  <KeyBindings>... </KeyBindings>  
  <UsedCommands... </UsedCommands>  
  <Symbols>... </Symbols>  
</CommandTable>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|xmlns|必須。 XML 名前空間:<br /><br /> xmlns ="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"<br /><br /> xmlns:xs ="http://www.w3.org/2001/XMLSchema"|  
|language|任意。 Language 属性がすべての既定の言語を指定するため\<文字列 > コマンド テーブル内の要素。  言語が指定されていない場合は、現在のプロセスの言語が使用されます。<br /><br /> language ="en-us"|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[Extern 要素](../extensibility/extern-element.md)|任意。 コンパイラのプリプロセッサ ディレクティブが含まれています。|  
|[Include 要素](../extensibility/include-element.md)|任意。 コンパイルに含めるすべてのファイルへのパスが含まれています。|  
|[Define 要素](../extensibility/define-element.md)|任意。 名前と値を指定されたシンボルを定義します。|  
|[Commands 要素](../extensibility/commands-element.md)|任意。 他の要素すべてを含む VSPackage のすべてのコマンドを定義する親要素です。|  
|[CommandPlacements 要素](../extensibility/commandplacements-element.md)|任意。 ここで、コマンド バーのコマンドを配置するかを定義します。|  
|[VisibilityConstraints 要素](../extensibility/visibilityconstraints-element.md)|任意。 コマンドおよびツールバーの静的な可視性を判断します。|  
|[KeyBindings 要素](../extensibility/keybindings-element.md)|任意。 いずれかのコマンドの場合は、ショートカット キーの組み合わせを指定します。|  
|[UsedCommands 要素](../extensibility/usedcommands-element.md)|任意。 必要に応じて独自のバージョンの最初の他の Vspackage でサポートされている機能を実装する VSPackage を使用できます。|  
|[Symbols 要素](http://msdn.microsoft.com/en-us/f2ddd0aa-c3dd-439e-834d-28f136a27ffa)|任意。 シンボルのすべてのデータ--Guid、Id、およびなど--コンパイラが含まれています。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|なし||  
  
## <a name="see-also"></a>参照  
 [Visual Studio Command Table (.Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)