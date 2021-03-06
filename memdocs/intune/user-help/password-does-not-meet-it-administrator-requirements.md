---
title: Intune 登録済みデバイスのパスワード要件 | Microsoft Docs
description: この記事では、ネットワークにアクセスできるように組織のパスワード要件を満たす方法について説明します。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/27/2020
ms.topic: end-user-help
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: efb3c261-1f6c-4d39-bfa4-18661f8c59c7
searchScope:
- User help
ROBOTS: ''
ms.custom: intune-enduser, contperfq1
ms.collection: ''
ms.openlocfilehash: b9bdada31e280c7fdc8a5d7a5a0a4a7ab7d36ae3
ms.sourcegitcommit: 41e6e6b7f5c2a87aaf7f23d90d0f175dd63c0579
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2020
ms.locfileid: "89057289"
---
# <a name="device-password-requirements"></a>デバイスのパスワード要件  

デバイスのパスワードが組織のセキュリティ要件を満たしていない場合は、ポータル サイトからメッセージが送られてきます。 パスワードの要件は、お客様とお客様の組織のデータを不正アクセスから保護するために設定されています。 より安全なパスワードを作成するまでは、組織のネットワークへのアクセスがブロックされる可能性があります。  

ポータル サイトからはパスワード要件ごとに 1 件のメッセージが送信されるため、一度に複数のメッセージを受け取る場合があります。 メッセージをタップすると、詳細が表示されます (存在する場合)。  

この記事では、受信する可能性のあるパスワード関連のメッセージをすべて示し、それぞれの要件について OS プラットフォーム別に詳しく説明します。     

## <a name="change-password-passcode-pin"></a>パスワード、パスコード、PIN を変更する  

一般に、パスワード設定にアクセスするには、デバイスで設定アプリを開き、"*ロック画面*" または "*セキュリティ設定*" を探します。  

次の記事では、デバイスのパスワードを更新する方法について OS プラットフォーム別に説明しています。 特定のデバイスに関する最新の手順を入手するには、デバイスの製造元のヘルプ ドキュメントを参照してください。  

- [Windows 10 デバイスのパスワードを設定する](set-or-change-your-password-windows.md)  
- [iOS デバイスのパスコードを設定する](set-or-change-your-passcode-ios.md)  
- [Android デバイスの PIN またはパスワードを設定する](set-your-pin-or-password-android.md)  


> [!IMPORTANT]
> 要件を満たすようにパスワードを変更しても、依然として通知が送られてくる場合は、デバイスを再起動します。  

組織のパスワード要件に関する具体的な質問については、IT サポート担当者にお問い合わせください。  

## <a name="windows-10-password-requirements"></a>Windows 10 のパスワード要件

| メッセージ | 修正方法 |
|-----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| パスワードが必要です。 | パスワードを設定してください。 組織によって、デバイスのロックを解除するためのパスワードの入力が要求されています。 |
| パスワードが簡単すぎます。 |  1234 や 1111 など、連続する数字や繰り返しの数字がパスワードに含まれていないことを確認してください。 |
| パスワードが短すぎます。| より多くの文字を使用してパスワードを更新または設定します。 組織によって、パスワードが特定の長さであることが要求されています。 実際に何を選択するかはさまざまですが、要求できる最小の長さは 4 文字で、最大は 16 文字です。 |
| Password must only contain numbers.\(パスワードには数字のみ使用できます。\) | 数字だけを含むパスワードを設定します。|
| Password must only contain alphanumeric characters.\(パスワードには英数字のみ使用できます。\) | 数字と文字が混在するパスワードを設定します。|
| Password must contain complex characters.\(パスワードには複雑な文字が含まれる必要があります。\) | 数字、英大文字、および `$`、`%`、`#` のような記号など、複雑な文字を追加します。 他の人がパスワードを推測しにくいように、文字、数字、英数字以外の文字を組み合わせて使用することが組織によって要求されています。|  
| パスワードの有効期限が切れています。 | 新しいパスワードを設定します。 組織によって、一定の日数が経過した後にパスワードを変更することが要求されています。 |
| パスワードがごく最近に使用されました。 | 前に使ったことのないパスワードを選択してください。 組織によって、パスワードを再利用する前に一定の時間が経過していることが要求されています。 |

## <a name="ios-passcode-requirements"></a>iOS のパスコード要件

| メッセージ | 修正方法 |
|-----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| パスコードが必要です。| パスコードを設定します。 組織によって、デバイスのロックを解除するためのパスコードの入力が要求されています。 |
| パスコードが簡単すぎます。 |  1234 や 1111 など、連続する数字や繰り返しの数字がパスコードに含まれていないことを確認してください。 |
| パスコードが短すぎます。 | より多くの文字を使用してパスコードを更新または設定します。 組織によって、パスコードが特定の長さであることが要求されています。 実際に何を選択するかはさまざまですが、要求できる最小の長さは 4 文字で、最大は 14 文字です。 パスコードを変更すると、Apple から 6 文字以上を入力するように求めるプロンプトが表示される場合があります。このメッセージは、Apple システムのみの推奨事項です。 組織で要求されるのが 4 文字または 5 文字のパスコードである場合は、6 桁のパスコードを入力する必要はありません。|  
| Passcode must only contain numbers.\(パスコードには数字のみ使用できます。\) | 数字だけを含むパスコードを設定します。|
| Passcode must only contain alphanumeric characters.\(パスコードには英数字のみ使用できます。\)| 数字と文字が混在するパスコードを設定します。|
| Passcode must contain non-alphanumeric characters.\(パスコードには英数字以外の文字を含める必要があります。\) | `&`、`!`、`$`、`%`、`#` などの特殊文字を追加します。 他の人がパスコードを推測しにくいように、文字、数字、英数字以外の文字を組み合わせて使用することが組織によって要求されています。|
| パスコードが期限切れです。 | 新しいパスワードを設定します。 組織によって、一定の日数が経過した後にパスワードを変更することが要求されています。 |
| パスコードがごく最近に使用されました。| 前に使ったことのないパスコードを選択してください。 組織によって、パスコードを再利用する前に一定の時間が経過していることが要求されています。 |
|Touch ID または Face ID 認証が必要です。 | Touch ID または Face ID を設定します。 パスワードまたはクレジット カード情報にオートフィルを使用する前に、これらのいずれかの方法を使用して認証を行うことが組織によって要求されています。 | 

## <a name="macos-password-requirements"></a>macOS のパスワード要件
| メッセージ | 修正方法 |
|-----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| パスワードが必要です。 | パスワードを設定してください。 組織によって、デバイスのロックを解除するためのパスワードの入力が要求されています。 |
| パスワードが簡単すぎます。|  1234 や 1111 など、連続する数字や繰り返しの数字がパスワードに含まれていないことを確認してください。 |
| パスワードが短すぎます。 | より多くの文字を使用してパスワードを更新または設定します。 組織によって、パスワードが特定の長さであることが要求されています。|
| Password must only contain numbers.\(パスワードには数字のみ使用できます。\) | 数字だけを含むパスワードを設定します。|
| Password must only contain alphanumeric characters.\(パスワードには英数字のみ使用できます。\) | 数字と文字が混在するパスワードを設定します。|
| Password must contain non-alphanumeric characters.\(パスワードには英数字以外の文字を含める必要があります。\) | `&`、`!`、`$`、`%`、`#` などの特殊文字を追加します。 他の人がパスワードを推測しにくいように、文字、数字、英数字以外の文字を組み合わせて使用することが組織によって要求されています。|
| パスワードの有効期限が切れています。 | 新しいパスワードを設定します。 組織によって、一定の日数が経過した後にパスワードを変更することが要求されています。 |
| パスワードがごく最近に使用されました。 | 前に使ったことのないパスワードを選択してください。 組織によって、パスワードを再利用する前に一定の時間が経過していることが要求されています。 |

## <a name="android-password-requirements"></a>Android のパスワード要件
| メッセージ | 修正方法 |
|-----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| パスワードが必要です。 | パスワードまたは PIN を設定します。 組織によって、デバイスのロックを解除するためのパスワードの入力が要求されています。 |
| パスワードが簡単すぎます。 |  1234 や 1111 など、連続する数字や繰り返しの数字がパスワードまたは PIN に含まれていないことを確認してください。 |
| パスワードが短すぎます。 | より多くの文字を使用してパスワードを更新または設定します。 組織によって、パスワードが特定の長さであることが要求されています。|
| パスワードに数字を含める必要があります。 | 数字を含むパスワードまたは PIN を設定します。|
| パスワードに文字を含める必要があります。 | アルファベットの文字を含むパスワードを設定します。|
| Password must contain alphanumeric characters.\(パスワードには英数字文字を含める必要があります。\) | 数字と文字が混在するパスワードを設定します。|
| Password must contain alphanumeric characters and symbols.\(パスワードには英数字文字と記号を含める必要があります。\) | 文字、数字、および特殊文字 (`&`、`!`、`$`、`%`、`#` など) が混在するパスワードを設定します。 |
| Password must use biometric technology.\(パスワードでは生体認証テクノロジを使用する必要があります。\)| 指紋や顔認識などの生体認証を使用するようにデバイスを設定します。
| パスワードの有効期限が切れています。 | 新しいパスワードを設定します。 組織によって、一定の日数が経過した後にパスワードを変更することが要求されています。 |
| パスワードがごく最近に使用されました。 | 前に使ったことのないパスワードを選択してください。 組織によって、パスワードを再利用する前に一定の時間が経過していることが要求されています。 |

## <a name="next-steps"></a>次のステップ
パスワードを更新した後もパスワードに関連するメッセージが表示される場合は、デバイスを再起動してみてください。 

サポートが必要な場合は、 IT サポート担当者にお問い合わせください。 連絡先情報については、[ポータル サイト Web サイト](https://go.microsoft.com/fwlink/?linkid=2010980)をご確認ください。  


