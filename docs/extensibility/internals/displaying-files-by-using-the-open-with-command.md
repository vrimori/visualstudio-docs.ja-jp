---
title: コマンドで開く を使用してファイルを表示する |Microsoft ドキュメント
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
ms.openlocfilehash: 9c708bb5a510748b08cac5b46b6829b908e74e0a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="displaying-files-by-using-the-open-with-command"></a>コマンドで開く を使用してファイルを表示します。
プロジェクトを表示するための IDE を求めることができます、**ファイルを開く** ダイアログ ボックス。 この要求は、標準のエディターの選択を含むファイルを開くかどうかを求めるメッセージを表示します。 次の手順では、このプロセスについて説明します。  
  
1.  プロジェクトの呼び出し<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>、OSE_UseOpenWithDialog の値を指定する、`OSEOpenDocEditor`パラメーター。  
  
2.  ドキュメントのファイル名拡張子に基づいた、IDE でレジストリに一覧表示するエディターは、指定されたドキュメントを開くを確認しのこの情報を表示、**ファイルを開く** ダイアログ ボックス。  
  
    > [!NOTE]
    >  含める必要がある組み込みエディターのプロジェクト、**ファイルを開く** ダイアログ ボックスは、このような各エディターのエディター ファクトリを登録する必要があります。 組み込みエディター機能の実装で実施されるプロジェクトの特定の種類と共に、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>メソッドです。 IDE では、主要なテキスト エディターとバイナリ エディターの組み込みエディター ファクトリがあります。 IDE では、各登録済みの Windows ファイルの関連付けの代わりには、エディター ファクトリのインスタンスも作成します。 このようなファイルの例では、Microsoft Word がします。  
  
3.  ユーザーがから項目を選択するとすぐに、**ファイルを開く**ダイアログ ボックスで、IDE が呼び出すことによってドキュメントを開く<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>メソッドです。 詳細については、次を参照してください。[する方法: 開いている標準エディター](../../extensibility/how-to-open-standard-editors.md)です。  
  
## <a name="see-also"></a>関連項目  
 [開くと、プロジェクト項目の保存](../../extensibility/internals/opening-and-saving-project-items.md)   
 [ファイルを開くコマンドを使用してファイルを表示します。](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)   
 [方法: 標準のエディターを開く](../../extensibility/how-to-open-standard-editors.md)