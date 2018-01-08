---
title: "ファイルを開くコマンドを使用してファイルを表示する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 75d714399f851aa479f398064e576790c793fffa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="displaying-files-by-using-the-open-file-command"></a>ファイルを開くコマンドを使用してファイルを表示します。
次の手順では、IDE を処理する方法について説明する、**ファイルを開く**で使用できるコマンド、**ファイル**でメニュー[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 手順では、プロジェクトがこのコマンドからの呼び出しに応答する方法についても説明します。  
  
 ユーザーがクリックしたとき、**ファイルを開く**コマンドを**ファイル** メニューからファイルを選択して、**ファイルを開く**ダイアログ ボックスで、次の処理が行われます。  
  
1.  実行中のドキュメント テーブルを使用して、IDE は、ファイルが既にプロジェクトで開いているかどうかを判断します。  
  
    -   ファイルが開いている場合は、IDE は、ウィンドウを resurfaces です。  
  
    -   ファイルが開いていない場合、IDE によって呼び出さ<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>するプロジェクトは、ファイルを開くことができますを決定するには、各プロジェクトのクエリを実行します。  
  
        > [!NOTE]
        >  プロジェクトの実装で<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>プロジェクトがファイルを開きますレベルを示す優先順位値を指定します。 優先順位の値がで提供される、<xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>列挙します。  
  
2.  各プロジェクトは、優先度レベルを示す重要度で応答ファイルをプロジェクトに配置します。  
  
3.  IDE では、次の条件を使って、どのプロジェクトが、ファイルを開きを決定します。  
  
    -   優先順位が高い (DP_Intrinsic) に応答するプロジェクトでは、ファイルが開きます。 複数のプロジェクトは、この優先順位で応答する場合、応答する最初のプロジェクトはファイルを開きます。  
  
    -   優先順位が高い (DP_Intrinsic) がないプロジェクトの応答が、同じ、低い優先順位で応答するすべてのプロジェクト、作業中のプロジェクトは、ファイルを開きます。 アクティブなプロジェクトがない場合は、初めてのプロジェクトを応答には、ファイルを開きます。  
  
    -   ファイル (DP_Unsupported) の所有権を要求しているプロジェクトはありません、その他のファイル プロジェクトでは、ファイルが開きます。  
  
         その他のファイル プロジェクトのインスタンスを作成すると、プロジェクトは常に DP_CanAddAsExternal 値を返します。 この値は、プロジェクト ファイルを開けることを示します。 このプロジェクトは、他のプロジェクトに含まれていない、開いているファイルの格納に使用されます。 このプロジェクト内の項目の一覧は保存されません。このプロジェクトは**ソリューション エクスプ ローラー**のみ使用する場合、ファイルを開きます。  
  
         その他のファイル プロジェクトが、ファイルが開かれることを示していない場合、プロジェクトのインスタンスは作成されていません。 ここでは、IDE は、その他のファイル プロジェクトのインスタンスを作成し、ファイルをプロジェクトに指示します。  
  
4.  IDE で認識するプロジェクト ファイルを開きとすぐに呼び出して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>そのプロジェクトでのメソッドです。  
  
5.  プロジェクトには、し、プロジェクト固有のエディターまたは標準のエディターを使用して、ファイルを開くためのオプションがあります。 詳細については、次を参照してください。[する方法: 開いているプロジェクトに固有のエディター](../../extensibility/how-to-open-project-specific-editors.md)と[する方法: 開いている標準エディター](../../extensibility/how-to-open-standard-editors.md)、それぞれします。  
  
## <a name="see-also"></a>参照  
 [コマンドで開く を使用してファイルを表示します。](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)   
 [開くと、プロジェクト項目の保存](../../extensibility/internals/opening-and-saving-project-items.md)   
 [方法: プロジェクトに固有のエディターを開く](../../extensibility/how-to-open-project-specific-editors.md)   
 [方法: 標準のエディターを開く](../../extensibility/how-to-open-standard-editors.md)