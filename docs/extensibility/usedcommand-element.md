---
title: "UsedCommand 要素 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "UsedCommands 要素 (VSCT XML スキーマ)"
  - "UsedCommands、VSCT XML スキーマ要素"
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# UsedCommand 要素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

別の .vsct ファイルで定義されているコマンドにアクセスする VSPackage を有効にします。 たとえば、標準を使用する、VSPackage **コピー** で定義されているコマンド、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] シェルでは、コマンドを追加するメニューまたはツールバー再実装せずします。  
  
## 構文  
  
```  
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|guid|必須です。 コマンドを識別する ID の GUID のペアの GUID です。|  
|ID|必須です。 コマンドを識別する ID の GUID のペアの ID です。|  
|状態|省略可能です。 「[条件付きの属性](../extensibility/vsct-xml-schema-conditional-attributes.md)」を参照してください。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|なし||  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[UsedCommands 要素](../extensibility/usedcommands-element.md)|UsedCommand 要素をグループ化とその他の UsedCommands のグループ化します。|  
  
## 解説  
 コマンドを追加することで、 `<UsedCommands>` 要素、VSPackage に通知、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 環境 VSPackage にコマンドが必要です。 追加する必要があります、 `<UsedCommand>` 、パッケージが必要とする任意のコマンドの要素は、すべてのバージョンと Visual Studio の構成に含めないことがあります。 たとえば、パッケージが Visual C に固有のコマンドを呼び出す場合のコマンドは、されません Visual Web Developer のユーザーが使用できる指定しない限り、 `<UsedCommand>` コマンドの要素。  
  
## 使用例  
  
```  
<UsedCommands> <UsedCommand guid="guidVSStd97" id="cmdidCut"/> <UsedCommand guid="guidVSStd97" id="cmdidCopy"/> <UsedCommand guid="guidVSStd97" id="cmdidPaste"/> </UsedCommands>  
```  
  
## 参照  
 [UsedCommands 要素](../extensibility/usedcommands-element.md)   
 [Visual Studio コマンド テーブル \(します。Vsct\) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)