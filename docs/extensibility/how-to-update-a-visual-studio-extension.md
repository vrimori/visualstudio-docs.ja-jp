---
title: '方法: Visual Studio の拡張の更新 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c37f26ed8215bb7eac360c978ba902c8e95975ba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134683"
---
# <a name="how-to-update-a-visual-studio-extension"></a>方法: Visual Studio の拡張の更新
使用して、システムに Visual Studio 拡張機能を更新することができます**拡張機能と更新プログラム**更新されたバージョンをインストールします。 拡張機能の更新バージョンを作成する場合は、することを示します VSIX マニフェストのバージョン番号のインクリメントで更新します。  
  
 入力方向の拡張機能の VSIX マニフェストがある同じ場合に更新プログラムがインストールされている`ID`としてインストールされていると、高い`Version`数。 場合、`Version`数が、同じまたは低いほど、このパッケージをインストールすることはできません。 場合、`ID`値が一致しない場合、まだインストールされていないパッケージは、別個の拡張機能として認識します。  
  
 開発時に競合を防ぐため、進行中で拡張機能の以前のバージョンをアンインストールしてもアンインストールまたは競合する可能性のあるその他のすべての拡張機能を無効にお勧めします。  
  
### <a name="to-update-an-extension-on-your-system"></a>システム上の拡張機能を更新するには  
  
1.  **[ツール]** メニューの **[拡張機能と更新プログラム]** をクリックします。  
  
2.  左側のウィンドウでをクリックして**更新**です。  
  
3.  中央のペインでをインストールする更新プログラムをクリックします。  
  
     更新された拡張機能のバージョン番号は、右ウィンドウで、その他の情報と共に表示されます。  
  
4.  右側のペインの下部には、をクリックして**更新**です。  
  
### <a name="to-publish-an-update-of-an-extension"></a>拡張機能の更新を発行するには  
  
1.  Visual Studio で、拡張機能を更新するためのソリューションを開きます。 変更を行います。  
  
    > [!IMPORTANT]
    >  署名されていないすべてのユーザーの拡張機能は自動的に更新されません。 常に、拡張機能に署名する必要があります。  
  
2.  **ソリューション エクスプ ローラー**source.extension.manifest を開きます。  
  
3.  マニフェスト デザイナーでの数値の値を大きく、**バージョン**フィールドです。  
  
4.  ソリューションを保存し、ビルドします。  
  
5.  (プロジェクトの \bin\Debug\ フォルダー) に新しい .vsix ファイルをアップロード、 [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) Web サイトです。  
  
     拡張機能の以前のバージョンを持つユーザーが開いたとき**拡張機能と更新**、新しいバージョンが表示されます、**更新**一覧で、ツールが自動的に更新プログラムを探すように設定されています。  
  
     有効にするにまたはの下部にある更新プログラムの自動チェックを無効にすることができます、**更新**ペイン (**使用可能な更新プログラムの自動検出を有効または無効に**)、変更、**の確認更新プログラム**設定**ツール/オプション/環境/拡張機能と更新プログラム**です。  
  
    > [!NOTE]
    >  Visual Studio 2015 更新プログラム 2 より、ユーザー単位の拡張機能を自動更新するか、すべてのユーザー拡張機能を更新するか、両方を行うか (初期設定) 指定できます (**[ツール]、[オプション]、[環境]、[拡張機能と更新プログラム]**)。  
  
## <a name="see-also"></a>関連項目  
 [VSIX パッケージの構造](../extensibility/anatomy-of-a-vsix-package.md)   
 [Visual Studio 拡張機能の検索と使用](../ide/finding-and-using-visual-studio-extensions.md)
