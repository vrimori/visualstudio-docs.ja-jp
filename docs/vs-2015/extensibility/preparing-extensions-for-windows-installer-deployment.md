---
title: Windows インストーラーの配置の拡張機能の準備 |Microsoft Docs
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
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b83e7d59e17b91e3a47625917de4ec7366f8389d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538068"
---
# <a name="preparing-extensions-for-windows-installer-deployment"></a>Windows インストーラーの配置に関する拡張機能を準備する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[を準備する拡張機能の Windows インストーラーの配置](https://docs.microsoft.com/visualstudio/extensibility/preparing-extensions-for-windows-installer-deployment)します。  
  
Windows インストーラー パッケージ (MSI) を使用して、VSIX パッケージを配置することはできません。 ただし、MSI の展開用の VSIX パッケージの内容を抽出することができます。 このドキュメントでは、プロジェクトの既定の出力は、セットアップ プロジェクトに含めることの VSIX パッケージを準備する方法を示します。  
  
## <a name="preparing-an-extension-project-for-windows-installer-deployment"></a>Windows インストーラーの配置の拡張機能プロジェクトを準備します。  
 セットアップ プロジェクトに追加する前に、新しい拡張機能プロジェクトに次の手順を実行します。  
  
#### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Windows インストーラーの配置の拡張機能プロジェクトを準備するには  
  
1.  VSPackage、MEF コンポーネント、エディターの表示要素、または VSIX マニフェストを含むその他の機能拡張プロジェクトの種類を作成します。  
  
2.  VSIX マニフェスト、コード エディターで開きます。  
  
3.  VSIX マニフェストの InstalledByMsi 要素設定`true`します。 VSIX マニフェストの詳細については、次を参照してください。 [VSIX 拡張機能スキーマ 2.0 リファレンス](../extensibility/vsix-extension-schema-2-0-reference.md)します。  
  
     これは、VSIX インストーラーが、コンポーネントをインストールしようとすることを防ぎます。  
  
4.  プロジェクトを右クリックして**ソリューション エクスプ ローラー**クリック**プロパティ**します。  
  
5.  選択、 **VSIX**タブ。  
  
6.  チェック ボックスをオン**次の場所にコピー VSIX コンテンツ**セットアップ プロジェクトは、ファイルを集荷するパスを入力します。  
  
## <a name="extracting-files-from-an-existing-vsix-package"></a>既存の VSIX パッケージからファイルを抽出  
 ソース ファイルを持っていない場合は、セットアップ プロジェクトに既存の VSIX パッケージのコンテンツを追加する手順を実行します。  
  
#### <a name="to-extract-files-from-an-existing-vsix-package"></a>既存の VSIX パッケージからファイルを抽出するには  
  
1.  名前を変更します。拡張機能を含む VSIX ファイル*filename*に .vsix *filename*.zip します。  
  
2.  ディレクトリに .zip ファイルの内容をコピーします。  
  
3.  [Content_types] .xml ファイルをディレクトリから削除します。  
  
4.  前の手順で示すように、VSIX マニフェストを編集します。  
  
5.  セットアップ プロジェクトに、残りのファイルを追加します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio インストーラーの配置](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [チュートリアル: カスタム アクションの作成](http://msdn.microsoft.com/en-us/4bd4b63a-2b91-431e-839c-5752443f0eaf)

