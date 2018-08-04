---
title: 開く を使用してコマンド ファイルの表示 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6983e9ee7b7cc88efb4870ab0836b856621aeeee
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497529"
---
# <a name="display-files-by-using-the-open-with-command"></a>プログラムから開くコマンドを使用してファイルを表示します。
プロジェクトを表示するための IDE を問い合わせることができる、**プログラムから開く** ダイアログ ボックス。 この要求には、ユーザーを標準のエディターの選択範囲を持つファイルを開くことが求められます。 次の手順では、このプロセスについて説明します。  
  
1.  プロジェクト呼び出し<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>の値を指定する`OSE_UseOpenWithDialog`の`OSEOpenDocEditor`パラメーター。  
  
2.  IDE、ドキュメントのファイル名拡張子に基づいて、レジストリに一覧表示するエディターは、指定されたドキュメントを開くかを決定およびでは、この情報が表示されます、**ファイルを開く** ダイアログ ボックス。  
  
    > [!NOTE]
    >  プロジェクトに含める必要がある組み込みのエディターを**プログラムから開く** ダイアログ ボックスはそのような各エディターのエディター ファクトリを登録する必要があります。 組み込みエディター機能の実装で実施されるプロジェクトの特定の種類と共に、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>メソッド。 IDE では、コアのテキスト エディターとバイナリ エディターの組み込みエディター ファクトリがあります。 IDE には、各登録済みの Windows ファイルの関連付けの代わりには、エディター ファクトリのインスタンスも作成します。 このようなファイルの例は、Microsoft Word です。  
  
3.  ユーザーがから項目を選択するとすぐ、**プログラムから開く** ダイアログ ボックスで、IDE が呼び出すことによってドキュメントを開く<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>メソッド。 詳細については、次を参照してください。[方法: 標準のエディターを開く](../../extensibility/how-to-open-standard-editors.md)します。  
  
## <a name="see-also"></a>関連項目  
 [開き、プロジェクト項目の保存](../../extensibility/internals/opening-and-saving-project-items.md)   
 [ファイルを開くコマンドを使用してファイルを表示します。](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)   
 [方法: 標準のエディターを開く](../../extensibility/how-to-open-standard-editors.md)
