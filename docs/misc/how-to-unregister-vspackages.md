---
title: "方法: VSPackage の登録解除 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "サンプル アプリケーション [Visual Studio SDK]、アンインストール"
  - "セットアップ、VSPackage"
ms.assetid: b51522f0-c033-4d93-b928-2171a953032b
caps.latest.revision: 14
caps.handback.revision: 14
manager: "douge"
---
# 方法: VSPackage の登録解除
既定では、Vspackage をビルドすると、外部の実験用レジストリ ハイブに登録されます。 実験用ハイブは、実験後に維持しておくつもりのない VSPackage でいっぱいになっている可能性があります。  
  
 実験用ハイブに登録されているすべてのパッケージを削除するには、CreateExpInstance ツールで \/Reset オプションを使用して、ハイブをリセットします。 詳細については、「[実験用インスタンス](../extensibility/the-experimental-instance.md)」を参照してください。  
  
## 個別の VSPackage の登録解除  
  
#### アンマネージ VSPackage の登録を解除するには  
  
1.  **\[スタート\]**、**\[ファイル名を指定して実行\]** の順にクリックし、「`regsvr32 /u` *pathToVSPackage.dll*」と入力して、次に、\[OK\] をクリックします。  
  
 アンマネージ VSPackages には自己登録コードが含まれているため、regsvr32 ユーティリティを使用して、それらの登録を解除することができます。  
  
#### マネージ VSPackage の登録を解除するには  
  
1.  **\[スタート\]**、**\[ファイル名を指定して実行\]** の順にクリックし、「*Visual Studio SDK インストール パス*`\EnvSDK\tools\bin\x86\regpkg /unregister` *pathToVSPackage.dll*」と入力して、次に、\[OK\] をクリックします。  
  
 RegPkg ツールは、マネージ VSPackage に埋め込むことができる登録属性を読み取ります。**\/unregister** スイッチは、レジストリから情報を削除するよう RegPkg に指示します。  
  
## 参照  
 [Visual Studio Integration Samples](http://msdn.microsoft.com/ja-jp/b5dbf078-3af2-4fed-a1ea-171e4ee73a43)