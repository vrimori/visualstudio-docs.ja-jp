---
title: CommandTable 要素 |Microsoft Docs
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
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 87b755ac0dbe7e10cfe52693840101729ab32069
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49241203"
---
# <a name="commandtable-element"></a>CommandTable 要素
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

CommandTable は、.vsct ファイルのルート要素です。 これは、実際のレイアウトと、IDE に VSPackage を提供するコマンドの種類を定義するファイルです。 コマンドは、メニュー項目、メニューのツールバー、およびコンボ ボックスに含めることができます。 詳細については、「 [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)」を参照してください。  
  
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
|language|任意。 言語属性がすべての既定の言語を指定するため\<文字列 > コマンド テーブル内の要素。  言語が指定されていない場合は、現在のプロセスの言語が使用されます。<br /><br /> language ="英語-米国"|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[Extern 要素](../extensibility/extern-element.md)|任意。 コンパイラのプリプロセッサ ディレクティブが含まれています。|  
|[Include 要素](../extensibility/include-element.md)|任意。 コンパイルに含める任意のファイルへのパスが含まれています。|  
|[Define 要素](../extensibility/define-element.md)|任意。 その名前と値のシンボルを定義します。|  
|[Commands 要素](../extensibility/commands-element.md)|任意。 すべての他の要素を含む VSPackage のすべてのコマンドを定義する親要素です。|  
|[CommandPlacements 要素](../extensibility/commandplacements-element.md)|任意。 コマンド バーで、コマンドが配置されるかを定義します。|  
|[VisibilityConstraints 要素](../extensibility/visibilityconstraints-element.md)|任意。 コマンドとツールバーの静的な可視性を判断します。|  
|[KeyBindings 要素](../extensibility/keybindings-element.md)|任意。 コマンドのショートカット キーの組み合わせを指定します。|  
|[UsedCommands 要素](../extensibility/usedcommands-element.md)|任意。 必要に応じてその他の Vspackage で最初にサポートされる機能の独自のバージョンを実装するために VSPackage を使用できます。|  
|[Symbols 要素](http://msdn.microsoft.com/en-us/f2ddd0aa-c3dd-439e-834d-28f136a27ffa)|任意。 コンパイラのシンボル データ--Guid、Id、およびなど--が含まれています。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|なし||  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio Command Table (.Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

