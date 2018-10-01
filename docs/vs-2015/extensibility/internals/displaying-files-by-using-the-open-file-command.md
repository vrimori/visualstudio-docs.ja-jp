---
title: ファイルを開くコマンドを使用してファイルの表示 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 139eb83f2260c44a3e0f8c50868d42aca8160694
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547824"
---
# <a name="displaying-files-by-using-the-open-file-command"></a>ファイルを開くコマンドを使用したファイルの表示
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Open File コマンドを使用してファイルを表示する](https://docs.microsoft.com/visualstudio/extensibility/internals/displaying-files-by-using-the-open-file-command)します。  
  
次の手順では、IDE を処理する方法について説明します、**ファイルを開く**コマンドで使用される、**ファイル**でメニュー [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。 また、プロジェクトがこのコマンドから発信された通話に応答する方法も説明します。  
  
 ユーザーがクリックすると、**ファイルを開く**コマンドを**ファイル** メニューからファイルを選択して、**ファイルを開く**ダイアログ ボックスで、次の処理が行われます。  
  
1.  実行中のドキュメントのテーブルを使用して、IDE は、ファイルは既にプロジェクトで開いているかどうか判断します。  
  
    -   ファイルが開いている場合は、ウィンドウが resurfaces IDE。  
  
    -   ファイルが開いていない場合、IDE によって呼び出さ<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>プロジェクトは、ファイルを開くことを確認するには、各プロジェクトのクエリを実行します。  
  
        > [!NOTE]
        >  プロジェクトの実装で<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>、位置、プロジェクトが開き、ファイル レベルを示す優先順位値を指定します。 優先度の値がで提供される、<xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>列挙体。  
  
2.  各プロジェクトは、重要度を示す優先順位の応答ファイルを開くプロジェクトの中にかかります。  
  
3.  IDE では、次の条件を使って、プロジェクト ファイルを開きを決定します。  
  
    -   最高の優先順位 (DP_Intrinsic) で応答するプロジェクトでは、ファイルを開きます。 この優先順位を持つ 1 つ以上のプロジェクトが応答する場合、応答する最初のプロジェクトは、ファイルを開きます。  
  
    -   同じ、低い優先順位で応答するすべてのプロジェクトを最高の優先順位 (DP_Intrinsic) でないプロジェクトが応答の場合は、アクティブなプロジェクトは、ファイルを開きます。 アクティブなプロジェクトがない場合は、応答する最初のプロジェクトは、ファイルを開きます。  
  
    -   プロジェクトは、ファイル (DP_Unsupported) の所有権を主張しません、その他のファイル プロジェクトでは、ファイルが開きます。  
  
         その他のファイル プロジェクトのインスタンスを作成すると、プロジェクトは常に DP_CanAddAsExternal 値を返します。 この値は、プロジェクトにファイルを開くことを示します。 このプロジェクトは、他のプロジェクトにない開いているファイルを格納するために使用されます。 このプロジェクト内の項目の一覧は保持されません。このプロジェクトは**ソリューション エクスプ ローラー**のみ使用される場合、ファイルを開きます。  
  
         その他のファイル プロジェクトがファイルを開くことを表していない場合、プロジェクトのインスタンスは作成されていません。 この場合、IDE では、その他のファイル プロジェクトのインスタンスを作成し、ファイルを開くプロジェクトに指示します。  
  
4.  IDE は、プロジェクト ファイルを開くかを決定しますとすぐに呼び出して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>そのプロジェクトでのメソッド。  
  
5.  プロジェクトには、プロジェクト固有のエディターまたは標準のエディターを使用してファイルを開くオプションがあります。 詳細については、次を参照してください。[方法: 開いているプロジェクト固有のエディター](../../extensibility/how-to-open-project-specific-editors.md)と[方法: 開いているエディターを標準](../../extensibility/how-to-open-standard-editors.md)、それぞれします。  
  
## <a name="see-also"></a>関連項目  
 [開く を使用してコマンド ファイルを表示します。](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)   
 [開くと、プロジェクト項目の保存](../../extensibility/internals/opening-and-saving-project-items.md)   
 [方法: プロジェクトに固有のエディターを開く](../../extensibility/how-to-open-project-specific-editors.md)   
 [方法: 標準のエディターを開く](../../extensibility/how-to-open-standard-editors.md)

