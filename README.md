# HW7
第七次作业  

实时变焦  

Camera.Parameters parameters=cam.getParameters();
        parameters.setFocusMode(Camera.Parameters.FOCUS_MODE_CONTINUOUS_PICTURE);
手动变焦

findViewById(R.id.btn_zoom).setOnClickListener(v -> {
            //todo 调焦，需要判断手机是否支持
            Camera.Parameters p = mCamera.getParameters();
            p.setZoom(5);
            mCamera.setParameters(p);
        });

延时拍摄+开启闪光灯  

findViewById(R.id.btn_picture).setOnClickListener(v -> {
            //todo 拍一张照片
            new Thread(new ThreadShow()).start();
        });
class ThreadShow implements Runnable {

        @Override
        public void run() {
            try {
                Thread.sleep(3000);
                Camera.Parameters parameters = mCamera.getParameters();
                // 开启闪光灯
                parameters.setFlashMode(Camera.Parameters.FLASH_MODE_ON);
                mCamera.setParameters(parameters);
                mCamera.takePicture(null,null,mPicture);

            } catch (InterruptedException e) {
                e.printStackTrace();
            }

        }
    }



