---
title: "ツール ウィンドウを登録します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ツール ウィンドウの管理を登録します。"
  - "ツール ウィンドウを登録します。"
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# ツール ウィンドウを登録します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用して、ツール ウィンドウを登録する <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> と  <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>  
  
## 使用例  
  
```c#  
  
      [ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")] [ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)] [ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]  
[ProvideMenuResource(1000, 1)]  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]  
public class PackageToolWindow : Package  
{  
```  
  
 上記のコードで、 <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> PersistedWindowPane および DynamicWindowPane のツール ウィンドウを Visual Studio に登録します。 永続化されたツール ウィンドウをドッキングされにタブ付き **ソリューション エクスプ ローラー**, 、およびダイナミック\] ウィンドウで、既定の開始位置とサイズを指定します。 動的なウィンドウが行われます一時的なもので起動時に作成されていないことを示します。 これは、システム レジストリ内の ToolWindows キー DontForceCreate 値を書き込みます。 詳細については、「[ツール ウィンドウの表示構成](../extensibility/tool-window-display-configuration.md)」を参照してください。