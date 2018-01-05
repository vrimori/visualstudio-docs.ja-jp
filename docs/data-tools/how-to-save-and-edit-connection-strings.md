---
title: "方法: 接続文字列を保存して |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8ef3a2c-029c-423b-9d9e-a4f1add4f640
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: bb3ddcf8a4d1ac14b356bfabac2378ff345ef65b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-save-and-edit-connection-strings"></a>方法: 接続文字列を保存および編集する
Visual Studio アプリケーションで接続文字列 (アプリケーション設定とも呼ばれます)、アプリケーション構成ファイルに保存したり、アプリケーションに直接ハードコーディングできます。 接続文字列をアプリケーション構成ファイルに保存すると、アプリケーションの保守タスクが簡単になります。 接続文字列を変更する必要がある場合は、アプリケーション設定ファイルで接続文字列を更新できます (ソース コードで変更してアプリケーションをコンパイルし直す必要はありません)。

接続文字列内に機密情報 (パスワードなど) を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。 アプリケーション構成ファイルに保存された接続文字列は暗号化も難読化もされないため、第三者がファイルにアクセスしてコンテンツを表示する可能性があります。 データベースへのアクセスを制御する方法としては、Windows 統合セキュリティを使用する方が安全です。

Windows 統合セキュリティを使用しない環境で、データベースにユーザー名とパスワードが必要な場合、接続文字列からユーザー名とパスワードを削除できます。ただし、データベースに正常に接続するには、この情報をアプリケーションから提供する必要があります。 たとえば、ユーザーにこの情報を要求するダイアログ ボックスを作成し、実行時に接続文字列を動的にビルドできます。 この方法でも、情報がデータベースに送信される途中で傍受された場合は、セキュリティの問題が発生する可能性があります。 詳細については、「[接続情報の保護](/dotnet/framework/data/adonet/protecting-connection-information)」を参照してください。

## <a name="to-save-a-connection-string-from-within-the-data-source-configuration-wizard"></a>データ ソース構成ウィザードでの接続文字列を保存するには
**データ ソース構成ウィザード**、接続文字列を保存するアプリケーション構成ファイル ページで、接続を保存するオプションを選択します。

## <a name="to-save-a-connection-string-directly-into-application-settings"></a>接続文字列をアプリケーション設定に直接保存するには
- ソリューション エクスプ ローラーで、[マイ プロジェクト] アイコン (Visual Basic) または [プロパティ] アイコン (c#) を開くには、プロジェクト デザイナーをダブルクリックします。
- [設定] タブを選択します。
- 接続文字列の名前を入力します。 コードで接続文字列にアクセスするときにこの名前を参照します。
- (接続文字列) 型を設定します。
- アプリケーション設定のスコープのままにします。
- 値フィールドに、接続文字列を入力するかを開くには、接続文字列を作成する接続プロパティ ダイアログ ボックスの 値 フィールドで省略記号 (...) ボタンをクリックします。  

## <a name="editing-connection-strings-stored-in-application-settings"></a>アプリケーション設定に格納された接続文字列の編集
プロジェクト デザイナーを使用してアプリケーションの設定に保存されている接続情報を変更することができます。  

### <a name="to-edit-a-connection-string-stored-in-application-settings"></a>アプリケーション設定に格納された接続文字列を編集するには
- ソリューション エクスプ ローラーで、[マイ プロジェクト] アイコン (Visual Basic) または [プロパティ] アイコン (c#) を開くには、プロジェクト デザイナーをダブルクリックします。
- [設定] タブを選択します。
- 値フィールドにテキストを選択して編集する接続を見つけます。
- 値 フィールドで、接続文字列を編集または接続プロパティ ダイアログ ボックスとの接続を編集する 値 フィールドで省略記号 (...) ボタンをクリックします。  

## <a name="editing-connection-strings-for-datasets"></a>データセットの接続文字列の編集
各 TableAdapter はデータセット内の接続情報を変更することができます。  

### <a name="to-edit-a-connection-string-for-a-tableadapter-in-a-dataset"></a>データセットに TableAdapter の接続文字列を編集するには
- ソリューション エクスプ ローラーで、編集する接続があるデータセット (.xsd ファイル) をダブルクリックします。
- TableAdapter を編集する接続を持つクエリを選択します。
- [プロパティ] ウィンドウで、[接続] ノードを展開します。
- 接続文字列をすばやく変更するには、ConnectionString プロパティを編集または接続プロパティの下矢印をクリックして新しい接続を選択します。

## <a name="security"></a>セキュリティ
接続文字列内に機密情報 (パスワードなど) を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。 データベースへのアクセスを制御する方法としては、Windows 統合セキュリティを使用する方が安全です。
詳細については、「[接続情報の保護](/dotnet/framework/data/adonet/protecting-connection-information)」を参照してください。
  
## <a name="see-also"></a>関連項目
[接続の追加](../data-tools/add-new-connections.md)