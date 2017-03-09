---
title: "プロジェクト項目のアップグレード | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロジェクト項目のアップグレード"
  - "プロジェクト [Visual Studio SDK]、項目のアップグレード"
  - "プロジェクト項目 [Visual Studio]、アップグレード"
ms.assetid: 8af29dd4-eaf1-4b3c-b602-198e1a3dff23
caps.latest.revision: 14
caps.handback.revision: 14
manager: "douge"
---
# プロジェクト項目のアップグレード
実行しない項目のプロジェクト システムを追加したり管理する場合プロジェクトのアップグレード プロセスに参加する必要があります。  Crystal Reports はプロジェクト システムに追加できる項目の例です。  
  
 通常プロジェクト項目の実装はプロジェクト参照であり既に他のプロジェクトのプロパティをアップグレードするかどうかの確認がであることを認識するために必要なので完全にインスタンス化されアップグレードされたプロジェクトを使用する必要があります。  
  
### プロジェクトのアップグレードの通知を受け取るには  
  
1.  プロジェクト項目の実装の <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> フラグ \(vsshell80.idl で定義されている\) を設定します。  プロジェクト システムはアップグレード中であることを [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] シェルによって場合自動読み込み時にプロジェクト項目 VSPackage が発生します。  
  
2.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> のメソッドによって <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> のインターフェイスに指示します。  
  
3.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> のインターフェイスはプロジェクトのシステムの実装の後にアップグレード操作の完了を適用され新しいアップグレードされたプロジェクトが作成されます。  シナリオによっては<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> のインターフェイスは <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A><xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>または <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> のメソッドの後に発生します。  
  
### プロジェクト項目ファイルをアップグレードするには  
  
1.  よくプロジェクト項目の実装ファイルのバックアップのプロセスを管理する必要があります。  これは <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> のメソッドの `fUpgradeFlag` のパラメーターがバックアップしたファイルが 「 .old 」として指定された要素ファイルに沿って配置<xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> に設定されている side\-by\-side のバックアップ特にに適用します。  プロジェクトのアップグレード時に古いシステム時刻バックアップしたファイルが古いとして指定することもできます。  さらにこれを回避するために特定の手順を実行して上書きされることがあります。  
  
2.  プロジェクト項目がプロジェクトのアップグレードの通知を受け取る場合**Visual Studio 変換ウィザード**  が表示されます。  したがってウィザードの UI のアップグレード メッセージを表示するために <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> インターフェイスのメソッドを使用します。  
  
## 参照  
 [Visual Studio Conversion Wizard](http://msdn.microsoft.com/ja-jp/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [カスタム プロジェクトのアップグレード](../misc/upgrading-custom-projects.md)