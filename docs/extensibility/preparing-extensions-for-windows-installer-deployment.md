---
title: Windows インストーラーの配置の拡張機能の準備 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ef69ac45a090aa4395aa15d1395cff1665255b51
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639114"
---
# <a name="prepare-extensions-for-windows-installer-deployment"></a>Windows インストーラーの配置の拡張機能を準備します。
Windows インストーラー パッケージ (MSI) を使用して、VSIX パッケージを配置することはできません。 ただし、MSI の展開用の VSIX パッケージの内容を抽出することができます。 このドキュメントでは、プロジェクトの既定の出力は、セットアップ プロジェクトに含めることの VSIX パッケージを準備する方法を示します。  
  
## <a name="prepare-an-extension-project-for-windows-installer-deployment"></a>Windows インストーラーの配置の拡張機能プロジェクトを準備します。  
 セットアップ プロジェクトに追加する前に、新しい拡張機能プロジェクトに次の手順を実行します。  
  
### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Windows インストーラーの配置の拡張機能プロジェクトを準備するには  
  
1.  VSPackage、MEF コンポーネント、エディターの表示要素、または VSIX マニフェストを含むその他の機能拡張プロジェクトの種類を作成します。  
  
2.  VSIX マニフェスト、コード エディターで開きます。  
  
3.  設定、 `InstalledByMsi` VSIX マニフェストの要素`true`します。 VSIX マニフェストの詳細については、次を参照してください。 [VSIX 拡張機能スキーマ 2.0 リファレンス](../extensibility/vsix-extension-schema-2-0-reference.md)します。  
  
     これは、VSIX インストーラーが、コンポーネントをインストールしようとすることを防ぎます。  
  
4.  プロジェクトを右クリックして**ソリューション エクスプ ローラー**クリック**プロパティ**します。  
  
5.  選択、 **VSIX**タブ。  
  
6.  チェック ボックスをオン**次の場所にコピー VSIX コンテンツ**セットアップ プロジェクトは、ファイルを集荷するパスを入力します。  
  
## <a name="extract-files-from-an-existing-vsix-package"></a>既存の VSIX パッケージからファイルを抽出します。  
 ソース ファイルを持っていない場合は、セットアップ プロジェクトに既存の VSIX パッケージのコンテンツを追加する手順を実行します。  
  
### <a name="to-extract-files-from-an-existing-vsix-package"></a>既存の VSIX パッケージからファイルを抽出するには  
  
1.  名前の変更、*します。VSIX*ファイルから拡張機能を含む*filename.vsix*に*filename.zip*します。  
  
2.  内容をコピー、 *.zip*ディレクトリにファイル。  
  
3.  削除、 *[Content_types] .xml*ディレクトリからファイル。  
  
4.  前の手順で示すように、VSIX マニフェストを編集します。  
  
5.  セットアップ プロジェクトに、残りのファイルを追加します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio インストーラーの配置](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [チュートリアル: カスタム アクションを作成します。](http://msdn.microsoft.com/en-us/4bd4b63a-2b91-431e-839c-5752443f0eaf)