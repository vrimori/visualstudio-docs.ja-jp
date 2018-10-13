---
title: プロジェクト項目のアップグレード |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- upgrading project items
- projects [Visual Studio SDK], upgrading items
- project items [Visual Studio], upgrading
ms.assetid: 8af29dd4-eaf1-4b3c-b602-198e1a3dff23
caps.latest.revision: 14
manager: douge
ms.openlocfilehash: a9bf5307e2eabc2ba15c8e2dc8e1b1e0fadb11a0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49224095"
---
# <a name="upgrading-project-items"></a>プロジェクト項目のアップグレード
追加またはを実装していないプロジェクト システム内の項目を管理する場合は、プロジェクトのアップグレード プロセスに参加する必要があります。 Crystal Reports は、プロジェクト システムに追加できる項目の例を示します。  
  
 通常、プロジェクト項目の実装者は、参照は、どのようなプロジェクトとその他のプロジェクトのプロパティは何がアップグレードの決定を行う必要があるため、既に完全インスタンス化とアップグレードされたプロジェクトを活用します。  
  
### <a name="to-get-the-project-upgrade-notification"></a>プロジェクトのアップグレード通知を取得するには  
  
1.  設定、<xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading>プロジェクト項目の実装では、(vsshell80.idl で定義されている) フラグ。 これにより、プロジェクト項目を auto に VSPackage を読み込むときに、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]プロジェクト システムは、アップグレードの過程において、シェルを決定します。  
  
2.  お勧め、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>インターフェイスを使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A>メソッド。  
  
3.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>プロジェクト システムの実装のアップグレード操作が完了したら、新しいアップグレードされたプロジェクトが作成した後、インターフェイスが発生します。 シナリオによっては、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>インターフェイスが発生した後、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>、または<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A>メソッド。  
  
### <a name="to-upgrade-the-project-item-files"></a>プロジェクト項目のファイルをアップグレードするには  
  
1.  プロジェクト項目の実装で、ファイルのバックアップ プロセスを慎重に管理する必要があります。 サイド バイ サイドでバックアップの場合は、具体的には適用される場所、`fUpgradeFlag`のパラメーター、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>メソッドに設定されている<xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>".old"として指定される側のファイルにバックアップされたファイルを配置する場所。 プロジェクトがアップグレードされたシステム時刻よりも古いバックアップ ファイルは、古いものとして指定できます。 さらに、これを防ぐために特定の手順を実行していない限り、このを上書き可能性があります。  
  
2.  プロジェクト項目がプロジェクトのアップグレードの通知を取得時に、 **Visual Studio 変換ウィザード**が引き続き表示されます。 そのためのメソッドを使用する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger>ウィザードの UI にアップグレード メッセージを提供するインターフェイス。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio 変換ウィザード](http://msdn.microsoft.com/en-us/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [カスタム プロジェクトのアップグレード](../misc/upgrading-custom-projects.md)