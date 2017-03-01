---
title: "使用して、分離シェルを変更します。Vsct ファイル |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode, .vsct file
ms.assetid: 6d147c2d-10e9-400e-b8ce-5566287b41ba
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: a20b546c6e8d6d70a17d3d0bae575a5b2898d781
ms.lasthandoff: 02/22/2017

---
# <a name="modifying-the-isolated-shell-by-using-the-vsct-file"></a>使用して、分離シェルを変更します。Vsct ファイル
Visual Studio の分離シェル プロジェクトの UI プロジェクトには、どのアプリケーション グループと個々 のコマンドは、アプリケーションで使用を指定できる .vsct ファイルが含まれています。 変更されていない .vsct ファイルからの抜粋を次に示します。  
  
```  
<!-- <Define name="No_WindowListCommand"/> -->  
<!-- <Define name="No_MoreWindowsCommand"/> -->  
<!-- <Define name="No_PaneNextPaneCommand"/> -->  
<!-- <Define name="No_PanePrevPaneCommand"/> -->  
```  
  
 既定では、ほとんどのコマンドおよびコマンド グループが含まれています。 そのコマンドまたはグループのコメントを解除、コマンド プロンプトまたはコマンドのグループを除外します。  
  
 たとえば、削除するには、次のペインと前のウィンドウのコマンドをコメント解除します、`No_PaneNextPaneCommand`と`No_PanePrevPaneCommand`エントリ。  
  
```  
  
<Define name="No_PaneNextPaneCommand"/> <Define name="No_PanePrevPaneCommand"/>  
  
```  
  
 詳細な例はこれらのカスタマイズを参照してください。[チュートリアル: 基本的な分離シェル アプリケーションを作成する](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)です。  
  
## <a name="referenced-files"></a>参照先のファイル  
 アプリケーションの既定の .vsct ファイルは、次のファイルを参照します。 これらのファイルは、Visual Studio SDK インストール ディレクトリの \VisualStudioIntegration\Common\Inc\ サブディレクトリにあります。  
  
|ファイル|説明|  
|----------|-----------------|  
|wbids.h|Web 参照パッケージの識別情報が UI。|  
|AppIDCmdUsed.vsct|Visual Studio の UI の主な要素用のテーブルをコマンドです。|  
|EmulatorCmdUsed.vsct|Emacs エディターおよび Brief エディターのエミュレーションの UI 要素のコマンド テーブルです。|  
|Vsdebugguids.h|コマンドのオプション ページで、Visual Studio デバッガーの他の機能の Guid を定義します。|  
|VsDbgCmdUsed.vsct|デバッガーのコマンド テーブルです。|  
  
 AppIDCmdUsed.vsct ファイルには、アプリケーションの .vsct ファイルで定義されているシンボルに基づいて Visual Studio の UI 要素が含まれています。  
  
 詳細については、次を参照してください。 [XML コマンド テーブルの設計 (します。Vsct) ファイル](../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)と[VSCT XML スキーマ リファレンス](../extensibility/vsct-xml-schema-reference.md)します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio シェルの分離](../extensibility/visual-studio-isolated-shell.md)
