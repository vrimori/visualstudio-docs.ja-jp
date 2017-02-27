---
title: "ファイル名拡張子 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ファイルの拡張子"
  - "ファイル名拡張子"
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# ファイル名拡張子
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPackage のファイル拡張子を登録すると[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のバージョンにアプリケーションを関連付けます。  これは [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の複数のバージョンがコンピューターにインストールされている重要です。  
  
 VSPackage のファイル拡張子は関連するプログラム ID \(ProgID\) を指す既定値の HKEY\_CLASSES\_ROOT キーの下に登録されます。  
  
 次は .vcproj ファイル拡張子の登録情報の例です :  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] に関連付けられているファイルは製品のインストールが製品のバージョン間でファイル拡張子の関連付けを維持できるようにするバージョン付きの ProgID は`VisualStudio.vcproj.8.0` など\) です。  バージョン固有のProgID では問題なく標準動詞を開き編集などなどオーバーライドまたはオーバーライドされたを使用して [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の他のアプリケーションまたはバージョンによって異なります。  
  
 場合によってはファイル拡張子と関連付けられた ProgID は変更しないでください。  たとえば.htm のファイル拡張子 \(\=\) htmlfile progid の ProgID は .htm と .html のファイルと協力してオペレーティング システムの場所にハード コードで検証およびよく使用されます。  
  
## 参照  
 [サイド バイ サイド配置のファイル名拡張子を登録します。](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [ファイル名拡張子のファイル ハンドラーを指定します。](../extensibility/specifying-file-handlers-for-file-name-extensions.md)