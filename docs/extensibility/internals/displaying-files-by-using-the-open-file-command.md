---
title: ファイルを開くコマンドを使用してファイルの表示 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 59ff5d938c21c6344d1979fbfca94e8acb791db6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53964664"
---
# <a name="display-files-by-using-the-open-file-command"></a>ファイルを開くコマンドを使用してファイルを表示します。
次の手順では、IDE を処理する方法について説明します、**ファイルを開く**コマンドで使用される、**ファイル**でメニュー [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 また、プロジェクトがこのコマンドから発信された通話に応答する方法も説明します。  
  
 ユーザーがクリックすると、**ファイルを開く**コマンドを**ファイル** メニューからファイルを選択して、**ファイルを開く**ダイアログ ボックスで、次の処理が行われます。  
  
1.  実行中のドキュメントのテーブルを使用して、IDE は、ファイルは既にプロジェクトで開いているかどうか判断します。  
  
    -   ファイルが開いている場合は、ウィンドウが resurfaces IDE。  
  
    -   ファイルが開いていない場合、IDE によって呼び出さ<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>プロジェクトは、ファイルを開くことを確認するには、各プロジェクトのクエリを実行します。  
  
        > [!NOTE]
        >  プロジェクトの実装で<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>、位置、プロジェクトが開き、ファイル レベルを示す優先順位値を指定します。 優先度の値がで提供される、<xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>列挙体。  
  
2.  各プロジェクトは、重要度を示す優先順位の応答ファイルを開くプロジェクトの中にかかります。  
  
3.  IDE では、次の条件を使って、プロジェクト ファイルを開きを決定します。  
  
    -   最高の優先順位で応答するプロジェクト (`DP_Intrinsic`) ファイルを開きます。 この優先順位を持つ 1 つ以上のプロジェクトが応答する場合、応答する最初のプロジェクトは、ファイルを開きます。  
  
    -   プロジェクトを最も優先度が返されない場合 (`DP_Intrinsic`) が、アクティブなプロジェクト ファイルを開き、同じ、低い優先度のすべてのプロジェクトが応答します。 アクティブなプロジェクトがない場合は、応答する最初のプロジェクトは、ファイルを開きます。  
  
    -   プロジェクト ファイルの所有権を主張しない場合 (`DP_Unsupported`)、その他のファイル プロジェクト ファイルが開きます。  
  
         プロジェクトは常に応答値を持つ場合は、その他のファイル プロジェクトのインスタンスを作成すると、`DP_CanAddAsExternal`します。 この値は、プロジェクトにファイルを開くことを示します。 このプロジェクトは、他のプロジェクトにない開いているファイルを格納するために使用されます。 このプロジェクト内の項目の一覧は保持されません。このプロジェクトは**ソリューション エクスプ ローラー**のみ使用される場合、ファイルを開きます。  
  
         その他のファイル プロジェクトがファイルを開くことを表していない場合、プロジェクトのインスタンスは作成されていません。 この場合、IDE では、その他のファイル プロジェクトのインスタンスを作成し、ファイルを開くプロジェクトに指示します。  
  
4.  IDE は、プロジェクト ファイルを開くかを決定しますとすぐに呼び出して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>そのプロジェクトでのメソッド。  
  
5.  プロジェクトには、プロジェクト固有のエディターまたは標準のエディターを使用してファイルを開くオプションがあります。 詳細については、「[方法 :プロジェクトに固有のエディターを開く](../../extensibility/how-to-open-project-specific-editors.md)と[方法。標準のエディターを開く](../../extensibility/how-to-open-standard-editors.md)、それぞれします。  
  
## <a name="see-also"></a>関連項目  
 [プログラムから開くコマンドを使用してファイルを表示します。](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)   
 [開き、プロジェクト項目の保存](../../extensibility/internals/opening-and-saving-project-items.md)   
 [方法: 開いているプロジェクト固有のエディター](../../extensibility/how-to-open-project-specific-editors.md)   
 [方法: 標準のエディターを開く](../../extensibility/how-to-open-standard-editors.md)