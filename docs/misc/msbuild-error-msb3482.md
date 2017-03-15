---
title: "MSBuild エラー MSB3482 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.SignFile.SignToolError"
helpviewer_keywords: 
  - "MSB3482"
ms.assetid: fd09371f-2658-4534-affa-edb485575f1a
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3482
**MSB3482: 署名中にエラーが発生しました: '\<error\>'。**  
  
 ClickOnce 配置を使用して発行するか、または SignTool を使用してマニフェストに署名すると、SignTool によってこのエラーが生成されることがあります。 一般的な問題を以下に示します。  
  
 **署名中にエラーが発生しました: '値を null にすることはできません。 パラメーター名: strongNameKey。'**  
  
 このエラーは、ClickOnce 配置中にエラー一覧に表示される可能性があります。 この問題は無効な署名キーを選択することによって引き起こされます。 通常、非 RSA 暗号化キーを使用しようとしています。 SignTool は RSA キーの暗号化のみをサポートしています。  
  
 このエラーを解決するには、コード署名が有効である RSA 暗号化のキーを取得します。  
  
 **署名中にエラーが発生しました: '証明書チェーンは信頼されたルート機関として構築されませんでした。'**  
  
 このエラーは、ClickOnce 配置中にエラー一覧に表示される可能性があります。 問題は、ユーザーのコンピューターで信頼されていないチェーンまたはルート証明機関が証明書に含まれていることです。 これは通常、コンピューターから別のコンピューターに証明書\/キーを移動するときに発生します。  
  
 このエラーを解決するには、作成元である証明機関 \(CA\) の「ルート証明書」をインストールします。 通常は、CA ベンダーの Web サイトに移動し、必要に応じてもう一度ダウンロードします。  
  
 **署名中にエラーが発生しました: '...\\setup.exe に署名できませんでした。 SignTool エラー: ISignCode::Sign でエラーが返されました: 0x80880253 署名者の証明書は署名に使用できません。'**  
  
 このエラーは、ClickOnce 配置中にエラー一覧に表示される可能性があります。  
  
 問題の原因として可能性が高いのは、証明書が有効な日付の範囲外になっていることです。たとえば、期限切れの証明書の場合です。  
  
 このエラーを解決するには、有効な日付を含む更新された証明書を取得します。  
  
 証明書を更新する方法の詳細については、Microsoft サポート技術情報 \([http:\/\/support.microsoft.com](http://support.microsoft.com/kb/925521)\) の記事 925521「インストールの署名に使用された証明書の期限切れ後に、Visual Studio 2005 ClickOnce アプリケーションを更新しようとすると、エラー メッセージが表示される」を参照してください。  
  
 **キーセットが存在しません。**  
  
 .pfx ファイルと証明書の間に不整合がある可能性があります。 証明書の削除と再インストールや、.pfx ファイルの再作成を試してみてください。  
  
 **指定した状態で使用するためのキーが無効**  
  
 http:\/\/blogs.msdn.com\/b\/smondal\/archive\/2012\/05\/08\/an\-error\-occurred\-while\-signing\-key\-not\-valid\-for\-use\-in\-specified\-state.aspx を参照してください。  
  
 **'パラメーターが正しくありません。**  
  
 ビルドを実行しているサービスまたはユーザー アカウントは証明書をインポートとたものと異なりますか。 秘密キーの保護を必要とするローカル セキュリティ ポリシーの設定を無効にしてください。  次に、ビルドのユーザー アカウントの証明書を削除して、再インポートします。  
  
 **要求された操作を完了できません  コンピューターは委任に対して信頼される必要があり、現在のユーザー アカウントは、委任を許可するように構成する必要があります。**  
  
 [この MSDN ブログの投稿](http://technet.microsoft.com/en-us/library/cc782684\(v=ws.10\).aspx)を参照してください。  
  
## 参照  
 [コード署名の概要](https://msdn.microsoft.com/en-us/library/ms537361\(v=vs.85\).aspx)   
 [SignTool.exe \(署名ツール\)](../Topic/SignTool.exe%20\(Sign%20Tool\).md)   
 [\[署名\] ページ \(プロジェクト デザイナー\)](../Topic/Signing%20Page,%20Project%20Designer.md)   
 [方法: アセンブリに署名する \(Visual Studio\)](http://msdn.microsoft.com/ja-jp/f468a7d3-234c-4353-924d-8e0ae5896564)   
 [方法 : 厳密な名前でアセンブリに署名する](../Topic/How%20to:%20Sign%20an%20Assembly%20with%20a%20Strong%20Name.md)   
 [厳密な名前付きアセンブリ](../Topic/Strong-Named%20Assemblies.md)   
 [マネージ アプリケーションの厳密な名前の署名](http://msdn.microsoft.com/ja-jp/5fef3490-c519-4363-94fd-8b1ad260dab5)   
 [\<PackageFiles\> 要素](../deployment/packagefiles-element-bootstrapper.md)