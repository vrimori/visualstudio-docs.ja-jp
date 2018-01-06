---
title: "Windows インストーラーの配置の拡張機能の準備 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b72fc46d64034ddc22e929fb1a1eff26115cce70
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="preparing-extensions-for-windows-installer-deployment"></a>Windows インストーラーの配置の拡張機能の準備
Windows インストーラー パッケージ (MSI) を使用して、VSIX パッケージを配置することはできません。 ただし、MSI 展開用の VSIX パッケージの内容を抽出することができます。 このドキュメントが既定の出力はセットアップ プロジェクトに含めるのための VSIX パッケージ プロジェクトを準備する方法を示します。  
  
## <a name="preparing-an-extension-project-for-windows-installer-deployment"></a>Windows インストーラーの配置の拡張機能プロジェクトを準備します。  
 セットアップ プロジェクトに追加する前に、新しい拡張機能プロジェクトでこれらの手順を実行します。  
  
#### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Windows インストーラーの配置の拡張機能プロジェクトを準備するには  
  
1.  VSPackage、MEF コンポーネント、エディターの表示要素、または VSIX マニフェストを含むその他の機能拡張プロジェクトの種類を作成します。  
  
2.  コード エディターで、VSIX マニフェストを開きます。  
  
3.  VSIX マニフェストの InstalledByMsi 要素の設定`true`です。 VSIX マニフェストの詳細については、次を参照してください。 [VSIX 拡張機能スキーマ 2.0 リファレンス](../extensibility/vsix-extension-schema-2-0-reference.md)です。  
  
     これは、VSIX インストーラーが、コンポーネントをインストールしようとすることを防ぎます。  
  
4.  プロジェクトを右クリックして**ソリューション エクスプ ローラー**  をクリック**プロパティ**です。  
  
5.  選択、 **VSIX**タブです。  
  
6.  チェック ボックスを**次の場所にコピー VSIX コンテンツ**セットアップ プロジェクトは、ファイルを取得する場所へのパスを入力します。  
  
## <a name="extracting-files-from-an-existing-vsix-package"></a>既存の VSIX パッケージからファイルを抽出  
 ソース ファイルがあるない場合に、セットアップ プロジェクトに既存の VSIX パッケージのコンテンツを追加する手順を実行します。  
  
#### <a name="to-extract-files-from-an-existing-vsix-package"></a>既存の VSIX パッケージからファイルを抽出するには  
  
1.  名前を変更します。VSIX ファイルへの拡張機能を含む*filename*に .vsix *filename*.zip です。  
  
2.  .Zip ファイルの内容をディレクトリにコピーします。  
  
3.  [Content_types] .xml ファイルをディレクトリから削除します。  
  
4.  前の手順で示すように、VSIX マニフェストを編集します。  
  
5.  セットアップ プロジェクトに、残りのファイルを追加します。  
  
## <a name="see-also"></a>参照  
 [Visual Studio インストーラーの展開](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [チュートリアル: カスタム アクションの作成](http://msdn.microsoft.com/en-us/4bd4b63a-2b91-431e-839c-5752443f0eaf)