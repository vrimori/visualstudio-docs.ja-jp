---
title: "テスト ソース管理プラグインのガイド |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0fdab6cb0b259fe169a9ebd43c92158a5ce20d4b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="test-guide-for-source-control-plug-ins"></a>テスト ソース管理プラグインのガイド
このセクションでは、ソース管理のプラグインをテストするためのガイダンスを提供[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 広範な概要、最も一般的なテスト領域と同様の問題がある可能性があるより複雑な領域の一部が表示されます。 この概要はテスト_ケースの網羅するものではありません。  
  
> [!NOTE]
>  いくつかのバグ修正と最新の機能強化[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]既存ソース管理プラグインがないの以前のバージョンを使用しているときに発生した以前の問題が明らかに IDE[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 変更されていませんプラグインに以前のバージョンから場合でも、既存のソース管理プラグインのこのセクションに列挙された領域をテストすることを強くお勧め[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。  
  
## <a name="common-preparation"></a>共通の準備  
 使用したマシン[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]対象のソース管理プラグインがインストールされている、必要とします。 同様に構成されている 2 つ目のコンピューターは、テストのソース管理から開く の一部で使用できます。  
  
## <a name="definition-of-terms"></a>用語の定義  
 このテスト ガイドするために、次の用語の定義を使用します。  
  
 クライアント プロジェクト  
 いずれかのプロジェクトで使用できる型[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ソース管理の統合をサポートしている (たとえば、 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]、 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]、または[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)])。  
  
 Web プロジェクト  
 Web プロジェクトの 4 つの種類があります。 ファイル システム、ローカル IIS、リモートのサイトおよび FTP です。  
  
-   ローカル パスにファイル システムのプロジェクトが作成されますが、インターネット インフォメーション サービス (IIS)、UNC パスを使用して内部的にアクセスされ、クライアント プロジェクトと同様に、IDE 内からのソース管理下に配置することができますをインストールするのには必要ありません。  
  
-   ローカル IIS プロジェクトの場合は、ローカル コンピューターを指す URL に IIS が同じコンピューターにインストールされている、アクセスされるで動作します。  
  
-   リモート サイトのプロジェクトは、IIS サービスも作成されますが、IIS サーバー コンピューター上およびからではなく、ソース管理下に置かれた、内部、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE です。  
  
-   FTP のプロジェクトは、リモートの FTP サーバーからアクセスしますが、ソース管理下に配置することはできません。  
  
 参加リスト  
 ソリューションまたはプロジェクトをソース管理の他の語句。  
  
 バージョン ストア  
 ソース管理プラグイン API を通じてアクセスされているソース管理データベース。  
  
## <a name="test-areas-covered-in-this-section"></a>このセクションで取り上げたテスト区分  
  
-   [テスト範囲 1: ソース管理からに/開いてを追加します。](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)  
  
    -   ケース 1 a: ソース管理にソリューションを追加  
  
    -   ケース 1 b: ソース管理からソリューションを開く  
  
    -   ケース 1 c: ソース管理からソリューションを追加  
  
-   [テスト領域 2: ソース管理からの取得](../../extensibility/internals/test-area-2-get-from-source-control.md)  
  
-   [テストの領域 3: チェック アウト/チェック アウトを元に戻す](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)  
  
    -   ケース 3: チェック アウト/チェック アウトを元に戻す  
  
    -   ケース 3 a: チェック アウト  
  
    -   ケース 3 b: チェック アウトの切断  
  
    -   ケース 3 c: クエリの編集/クエリを保存 (QEQS)  
  
    -   サイレント チェック アウトの 3d を大文字:  
  
    -   ケース 3 e: チェック アウトを元に戻す  
  
-   [テスト領域 4: チェックイン](../../extensibility/internals/test-area-4-check-in.md)  
  
    -   ケース 4 a: 項目を変更  
  
    -   4b の場合: ファイルを追加します。  
  
    -   ケース 4 c: プロジェクトの追加  
  
-   [テスト領域 5: ソース管理の変更](../../extensibility/internals/test-area-5-change-source-control.md)  
  
    -   Case 5a: バインド  
  
    -   Case 5b: バインド解除  
  
    -   場合は 5 c: 再バインド  
  
-   [テスト領域 6: 削除](../../extensibility/internals/test-area-6-delete.md)  
  
-   [テスト領域 7: 共有](../../extensibility/internals/test-area-7-share.md)  
  
-   [テスト領域 8: プラグインの切り替え](../../extensibility/internals/test-area-8-plug-in-switching.md)  
  
    -   8 a の場合: 自動変更  
  
    -   Case 8b: ソリューションに基づく変更  
  
## <a name="see-also"></a>参照  
 [ソース管理プラグイン](../../extensibility/source-control-plug-ins.md)